Solution - CIA Agent Bourne Hacking Secrets Hackercise

The solution to the hackercise is given below, but we highly recommend that you try to 'hack' and solve it with the knowledge of Hacking Secrets that you have gained. If you are stuck, you can obviously look at the command(s) to run, but first try on your own.

As an agent, it is important that you read all instructions given. However, if you missed reading that you have to read the DEBRIEF message in the /home directory, you can follow the steps below to get there.

Type `ls`{{execute}}  and press enter.

You will see the listing of all the files in the directory with a file in there called README.txt.

Let us open and read the contents of the README.md file using the __cat__ command.
Type `cat README.md`{{execute}} and press enter.
Note: .md stands for markdown file.

You will see instructions to go to the 'home' directory as shown below.
`You need to go /home to begin.`

Let us navigate to the 'home' directory using the __cd__ command.
Type `cd home/`{{execute}} and press enter.

To list the contents of the 'home' directory, use the __ls__ command.
Type `ls`{{execute}} and press enter.

You will see that there is a file in there called 'DEBRIEF.md' and a folder name 'Duke'

Let us open and read the contents of the 'DEBRIEf.md' file using the __cat__ command.
Type `cat DEBRIEF.md`{{execute}} and press enter.
You should see a note addressed to you (Agent Bourne) instructing you that your first mission is to discover the password of a suspect known as 'Duke'

`Hello Agent Bourne

We have a mission for you.
We have learned that there is a cyber attack being planned.

All of the communications we were able to intercept are protected
using passwords, encoding, or other crypto mechanisms.

We have a lead on a suspect known only as Duke.
It seems as if Duke has infiltrated our systems and was found
lurking around hampshire. In it you may find some files to crack.

Your first mission is to discover Duke's account password etc.
Our Cyber Future depends on you.

Best Wishes Agent Bourne,
CyberShaolin Intelligence Agency (CIA)`

With your willingness to accept this mission, let us navigate into the 'Duke' directory using the __cd__ command.
Type `cd Duke`{{execute}} and press enter.

Once you are in the directory, use the __ls__ command to list the contents of that directory.
Type `ls`{{execute}} and press enter.

You should see three files - the README.md file, a zipped folder called hampshire.zip  and an etc_passwords.db file as shown below.
`README.md  etc_passwords.db  hampshire.zip`

Let us open and read the content of the README.md file.
Type `cat README.md`{{execute}} and press enter.
You should see the message
`You cannot proceed and get into Hampshire, until you crack my password /etc.`

In order to discover the password, we can use 'John' password cracker.
Type `john etc_passwords.db --show`{{execute}} and press enter.
You will see the message that 1 password hash was cracked.

`Duke:blackpanther:1000:1000:Frederick Joubert Duquesne,1913,XXX-XXX-1234,XXX-XXX-9876:/home/Duke:/bin/bash

1 password hash cracked, 0 left`

Closely reviewing that message, you will notice, that the password for the user __Duke__ is __blackpanther__.

Using this password, we can unzip the hampshire.zip file.

To unzip the hampshire.zip file,
Type `unzip hampshire.zip`{{execute}} and press enter.
You will be asked a password to unzip the file as shown below
`Archive:  hampshire.zip
   creating: hampshire/
[hampshire.zip] hampshire/spy_cities.txt password:`
Type in the previously cracked password (blackpanther) and press enter.
Note since you are typing in the password, you will not see any text on the screen.

Upon successfully entering the password and pressing enter, you will see that the hampshire.zip file is unzipped and the following files will be extracted and placed in a folder called 'hampshire'
`  inflating: hampshire/spy_cities.txt
  inflating: hampshire/shh.msg
  inflating: hampshire/ssh_duke.hash
  inflating: hampshire/.ssh_duke.pub
 extracting: hampshire/emails.zip
  inflating: hampshire/.ssh_duke`

Listing the contents of this directory using the __ls__ command, you will see that there is a new folder called 'hampshire' now present.

Navigate into the 'hampshire' folder using the __cd__ command.
Type `cd hampshire`{{execute}} and press enter.

List the content of this folder and you will find the following files.
`emails.zip  shh.msg  spy_cities.txt  ssh_duke.hash`

When you try to unzip the emails.zip using `unzip emails.zip` you will be asked for a password and the previously discovered password 'blackpanther' does not work.
You will need to find the password to unzip the emails.zip file.

Looking at that folder, looks like there is a secret message (shh.msg) in that folder that we can try to open using the __cat__ command.

Type `cat shh.msg`{{execute}} and press enter.
The message reads:
`In order to proceed, you need to quietly shh find the password that protects my stash, I mean hash.
You may want to explore the cities that spies like me hang out. You can take my "word(list)" for it.`

It seems like 'Duke' has generated his ssh_duke.hash file with a password and we can use the spy_cities.txt file as the wordlist to try and discover it using 'john'.
Type`john ssh_duke.hash -wordlist=spy_cities.txt`{{execute}}  and press enter.

You will see that a password was loaded from the wordlist and it was cracked. The password to unzip the emails.zip file is `bermuda` as shown below.
`Loaded 1 password hash (SSH [RSA/DSA/EC/OPENSSH (SSH private keys) 32/64])
Cost 1 (KDF/cipher [0=MD5/AES 1=MD5/3DES 2=Bcrypt/AES]) is 0 for all loaded hashes
Cost 2 (iteration count) is 1 for all loaded hashes
Will run 2 OpenMP threads
Note: This format may emit false positives, so it will keep trying even after
finding a possible candidate.
Press 'q' or Ctrl-C to abort, almost any other key for status
bermuda          (ssh_duke)
1g 0:00:00:00 DONE (2019-12-30 06:54) 20.00g/s 411620p/s 411620c/s 411620C/s Zumbrota..Zwolle
Session completed`

Now let us try to unzip the emails.zip file using the password 'bermuda'
Type `unzip emails.zip`{{execute}} and press enter.

You will be asked a password to unzip the file as shown below
`Archive:  emails.zip
   creating: emails/
[emails.zip] emails/TheBlackPanther.jpg password:`

Type in the previously cracked password (bermuda) and press enter.
Note since you are typing in the password, you will not see any text on the screen.

Upon successfully entering the password and pressing enter, you will see that the emails.zip file is unzipped and and the following files will be extracted and placed in a folder called 'emails'
` inflating: emails/TheBlackPanther.jpg
  inflating: emails/hack.msg`

Now navigate into the 'emails' folder using the __cd__ command.
Type `cd emails`{{execute}} and press enter.

List the contents of the emails folder using the __ls__ command.
Type `ls`{{execute}} and press enter.

You will see 2 files - one image file and the other a msg file.
`TheBlackPanther.jpg  hack.msg`

To read the contents of the hack.msg file, use the __cat__ command.
Type `cat hack.msg`{{execute}} and press enter.

You will see an email, but as you read this email till the end, you will learn that this is a fake email and that the real hack plan is hidden here.
There is also a clue at the end of the message .
`From: Zimmermann <a.z@gfo.de>
Date: January 19, 1917 at 04:11:00 AM CDT
To: Duke <duke@gfo.de>
Cc:
Subject: Fake Hack Plan

Attention Duke,

The cyber attack is planned against Britain and its allied forces is planned for:

April 01, 1917 1800 hrs.

Given below are the details of the cyber attack.

Start with the launch of the enigma virus followed by an amorous note from Melissa.
If you get stuck in any of those exploits, then unleash the Stux on the Network.

Auf Wiedersehen,
AZ

PS: You think you got us, the cyber attack is not to be executed on
April 01, 1917 at 6:00 PM as indicated above.
The real hack plan is hidden here.
TheBlackPanther strikes again.
To open hidden hack plan a password is needed, which you will get by solving the riddle below.

"I have a long sticky tongue,
I can roll my eyes independently in different directions,
I can change colors."
Who Am I?`

Since the real hack plan is hidden here, we can try to use the `ls -la` command to find hidden files.
Type `ls -la`{{execute}} and press enter.
You will notice that there are no other files other than the false hack.msg and TheBlackPanther.jpg.

Click on the Tab which reads `CIA Website` and a new browser window will open with the words
`Welcome to CyberShaolin Intelligence Agency (CIA)
Here you will see the picture of a the Black Panther, the moniker of a German Spy that the FBI used to call "The Duke"
[Image of a Black Panther is shown here.]

Black Panther Image Credits: kitty mcgritty`

It seems like German Spy Frederick Joubert Duquesne whom the FBI used to call the  'Duke' had hidden a secret message within the TheBlackPanther image using steganography. We need to extract that message from the TheBlackPanther image and for that we will need a passphrase.

From the fake email, we can guess that the animals which roll their eyes and can change colors are squids and chameleons. So, the password may be one of them.

To try and extract the secret message, using the __steghide__ command,
Type `steghide extract -sf TheBlackPanther.jpg`{{execute}} and press enter.

When you are prompted for the passphrase as shown below
`root@b43c55752244:/home/Duke/hampshire/emails# steghide extract -sf TheBlackPanther.jpg
Enter passphrase:`
try 'squid'. Note, you will not see any characters as it is a passphrase.
You will be informed that it was not possible to extract data with that passphrase! as shown below.
`steghide: could not extract any data with that passphrase!`

To try again, type the same command and try again.
Type `steghide extract -sf TheBlackPanther.jpg`{{execute}} and press enter.
This time try the passphrase 'chameleon'

You will notice that the hidden data in the TheBlackPanther.jpg file was extracted and written to a file named 'realHack.msg' as shown below.
`wrote extracted data to "realHack.msg".``

Let us open up the realHack.msg file using the __cat__ command.
Type `cat realHack.msg`{{execute}} and press enter.

You will see some text that would seems like it is gibberish (as shown below). It is actually encoded - encoded with base64 encoding, which is trivial to decode.
`RnJvbTogWmltbWVybWFubiA8YS56QGdmby5kZT4KRGF0ZTogSnVseSA0LCAyMDE5IGF0IDA0OjExOjAwIEFNIENEVApUbzogRHVrZSA8ZHVrZUBnZm8uZGU+CkNjOgpTdWJqZWN0OiBUaGUgUmVhbCBIYWNrIFBsYW4KLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0KQXR0ZW50aW9uIER1a2UsCgpUaGUgY3liZXIgYXR0YWNrIGlzIHBsYW5uZWQgYWdhaW5zdCBCcml0YWluIGFuZCBpdHMgYWxsaWVkIGZvcmNlcyBpcyBwbGFubmVkIGZvcjoKCkZlYiAyMCwgMjAyMCAxODAwIGhycy4KCkdpdmVuIGJlbG93IGFyZSB0aGUgZGV0YWlscyBvZiB0aGUgY3liZXIgYXR0YWNrLgpTdGFydCB3aXRoIHRoZSBsYXVuY2ggb2YgdGhlIGVuaWdtYSB2aXJ1cyBmb2xsb3dlZCBieSBhbiBhbW9yb3VzIG5vdGUgZnJvbSBNZWxpc3NhLgoKSWYgeW91IGdldCBzdHVjayBpbiBhbnkgb2YgdGhvc2UgZXhwbG9pdHMsIHRoZW4gdW5sZWFzaCB0aGUgU3R1eCBvbiB0aGUgTmV0d29yay4KCkF1ZiBXaWVkZXJzZWhlbiwKQVoKClBTOiBDb25ncmF0dWxhdGlvbnMuIFlvdSBoYXZlIHN1Y2Nlc3NmdWxseSBjb21wbGV0ZWQgdGhlIGhhY2tpbmctc2VjcmV0cyBoYWNrZXJjaXNlLg==

This message is top secret and encoded.
You would need to go to the cyber Base 64 to decode it.
AZ`

To decode the realHack.msg file, we can used the __base64 -d__ command.  
Type `base64 -d realHack.msg`{{execute}} and press enter.

You will now have the real Hack message decoded and displayed as shown.
`From: Zimmermann <a.z@gfo.de>
Date: July 4, 2019 at 04:11:00 AM CDT
To: Duke <duke@gfo.de>
Cc:
Subject: The Real Hack Plan

Attention Duke,

The cyber attack is planned against Britain and its allied forces is planned for:

Feb 20, 2020 1800 hrs.

Given below are the details of the cyber attack.
Start with the launch of the enigma virus followed by an amorous note from Melissa.

If you get stuck in any of those exploits, then unleash the Stux on the Network.

Auf Wiedersehen,
AZ

PS: Congratulations. You have successfully completed the hacking-secrets hackercise.N�base64: invalid input`

Congratulations, you have successfully completed the hacking secrets hackercise, agent Bourne.

The CyberShaolin Intelligence Agency (CIA) is proud of agents such as yourself.
