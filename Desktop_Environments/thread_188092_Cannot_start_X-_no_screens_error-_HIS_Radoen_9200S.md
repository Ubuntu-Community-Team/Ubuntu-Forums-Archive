---
title: "Cannot start X- no screens error- HIS Radoen 9200SE (ATI)"
date: 2006-06-03
forum: Desktop Environments
---

### Post by teataster on 2006-06-03
I have had this problem in Dapper since I upgraded from Breezy to Flight 3.

I have not been able to get the ati or fglrx drivers to work at all and can only use vesa which means I am stuck with 1024x768.  Had no problems in Breezy with fglrx at all.

I have followed the forums on this and followed many different suggestions, but with no joy.  I thought that there must be something left on my system from the previous attempts that I did not remove and so thought that a clean install of the Dapper gold CD would solve matters, but putting the CD in to my system tonight has had exactly the same result- X does not start and gives a 'no screens' error.  Hence, I have not gone through the pain of reinstalling as it seems it won't work.

I have seen others' posts that they have got 9200SE's to work, but I haven't yet.  The only lead I have is that it could be something to do with a clash with motherboard graphics when using a more modern card- can anyone help?    Am I liekly to have any success if I go through the hassle of a reinstall and then try the ATI drivers?

Any comments gratefully welcomed.

---

### Post by daller on 2006-06-04
From a terminal, run:

sudo dpkg-reconfigure xserver-xorg

Then you are prompted about alot of things...

Generally just keep clicking "enter" - but of course read what it prompt you!

After 10 minutes or so, you should be fine again!

Any questions? - bring 'em!

---

### Post by teataster on 2006-06-05
Sorry Daller- have done this at least 100 times but without luck!  Have tried just about every combination suggested with all 3 drivers and various customised xorg.conf files, but no success so far.

What I haven't tried yet is to go back to the Breezy drivers and see if that works- then that would identify whether the problem is with the drivers or the Dapper version of X.

---

### Post by teataster on 2006-06-07
I have now got proper resolution on my desktop- remembered I had an Nvidia card in another PC and swapped it with the ATI card.  No problems with the Nvidia driver so far other than minor glitches in bottom panel when set to transparent.

Would appreciate it if anyone can fix the ATI issue though...

---

### Post by underwater on 2006-06-07
[QUOTE=teataster]I have now got proper resolution on my desktop- remembered I had an Nvidia card in another PC and swapped it with the ATI card.  No problems with the Nvidia driver so far other than minor glitches in bottom panel when set to transparent.

Would appreciate it if anyone can fix the ATI issue though...[/QUOTE]
Post the xorg.conf for people to take a look at when configured and failing for ati or fglrx

---

### Post by teataster on 2006-06-07
This is an example of the many I have had.  The live CD version of 6.06 LTS gives the same error.

---

