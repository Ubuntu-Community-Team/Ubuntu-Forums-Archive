---
title: "Newbie: Strange xclip behaviour (not available for ordinary users)"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Jucas on 2005-12-14
Hi all. 
I just installed xclip (sudo apt-get install xclip) on breezy. Strangely, when returning to my usual user, xclip is not there.  I can use it with root priviledges, but not as an ordinary user. Man pages are available for both root and ordinary users.
A transcript of a couple of commands is given below

oyvindve@BanditAtWork:~$ nano temp
oyvindve@BanditAtWork:~$ xclip temp
bash: xclip: command not found
oyvindve@BanditAtWork:~$ sudo bash
root@BanditAtWork:~# xclip temp
root@BanditAtWork:~# xclip -out
This is the text from temp
root@BanditAtWork:~#

Anyone else have the same problem or is this because of some strange thing at my local machine?

&#216;yvind

Update: Found that adding 'export PATH=$PATH:/usr/X11R6/bin' to .bashrc fixed the problem. But shouldn't the installer have 
taken care of this?

---

