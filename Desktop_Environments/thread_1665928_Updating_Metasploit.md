---
title: "Updating Metasploit"
date: 2011-01-13
forum: Desktop Environments
---

### Post by mikeody on 2011-01-13
Whilst I have a reasonable amount of Ubuntu, I am very confused about an issue re updating my copy of Metasploit.
There have been a number of postings previously on this point but to be honest I havnt understood many of the responses.
As I understand it the command is either :

msfupdate [as root] or

sudo svn update /opt/metasploit3/msf3/

In both cases I am getting a similar response that refers to the 'working copy' of /opt/metasploit3/msf3 being "locked". With the svn option I am told to run svn cean-up but when I do that I start to become completely lost.

Can anyone advise please what all this means ? Logically I thought this was about permissions but it doesnt seem to be that at all.

A reply in words of one syllable would be great.
Thanks.

---

### Post by Closet on 2011-06-04
I know this is a bit of an old thread but it thought id post the answer here for future generations :). 

Its quite simple, just change directory to your msf3 folder using the "cd" command followed by the place the folder is located.

I.e
 cd /home/*username*/Documents/msf3

Then use the code:

svn update

takes a while to get started but it should run loads of codey stuf and end with updated to revision *number*.

---

