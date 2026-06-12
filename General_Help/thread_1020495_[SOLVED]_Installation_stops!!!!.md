---
title: "[SOLVED] Installation stops!!!!"
date: 2008-12-24
forum: General Help
---

### Post by charanpreethu on 2008-12-24
First I would like to say my comp configuration

AMD 64 x2 4000
1 gb ram
160 gb hd

   kubuntu installation stops at 82%..Message shown by it will be -scanning mirror..but installation doesnt proceed..How can I install??

---

### Post by gettinoriginal on 2008-12-24
Are you trying to install, or burn a Live CD ??  the scanning mirror message is a little confusing to me. :confused:

---

### Post by plucky on 2008-12-24
During the installation,if you have a network connection,the install will scan for the best mirror for your installation and update your sources.list file.


How long have you waited?
Is it a wireless connection or wired?
During the setup phase,did it find a network connection using dhcp?

If it is wireless,you could temporarily use a wired connection as that is most likely to work.If it is wired,you could try disconnecting it and installing without a network connection.

Did you test the integrity of the install CD?
Was the MD5sum of the ISO correct?

Good Luck

---

### Post by charanpreethu on 2008-12-24
I have wired connection..
  Yeah i tested the integrity of the cd its fine

now i will disconnect the network connection and try....

---

### Post by redilyn on 2008-12-24
I have this problem whenever I install with the network cable plugged in even though I have a 15mbit connection. If you wait 15-30minutes it will continue.

Best thing to do is install without a network cable plugged in.

---

### Post by charanpreethu on 2008-12-24
Done with installation....But it has come up with new problem..
I will get the loading( booting kubuntu) thing but after that screen goes blank....what to  do now???

---

### Post by plucky on 2008-12-24
> **charanpreethu said:**
> Done with installation....But it has come up with new problem..
I will get the loading( booting kubuntu) thing but after that screen goes blank....what to  do now???

That is usually a problem with the video card driver

If you get the grub menu select 'e' to edit the menu,use the arrows to move to the kernel line and select 'e' to edit the line and remove the splash and quiet in the kernel line that looks like this ```
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=03aa7483-5b8f-4c1e-bd09-5db055ead5eb ro quiet splash
``` Then select 'b' to continue the boot

 This should give you a scrolling text display until it reaches the login screen.This is only for this one boot as on any subsequent boot the menu.lst file will be used.

Does it reach the login screen?
Can you login?

If you can login,we will have to edit your menu.lst file to select an acceptable screen resolution to get rid of the blank screen.

Good Luck

---

### Post by charanpreethu on 2008-12-24
Ya its working fine thanks for replying.....


Now i have lot of question

1)How to play mp3,rm n all media files???
2)How to enable compiz?
3)Is there anything like synaptic manager in kubuntu???

---

### Post by plucky on 2008-12-24
> 1)How to play mp3,rm n all media files???

You might want to read this thread [url=http://ubuntuforums.org/showthread.php?t=766683&highlight=mp3+codecs[/url]

> 2)How to enable compiz?

Don't know

> 3)Is there anything like synaptic manager in kubuntu??? 

There is ,but it has been a long time since I had Kubuntu installed so can't remember.

Good Luck

---

### Post by gettinoriginal on 2008-12-24
For compiz:

System > Admin > Synaptic Package Manager, install CompizConfig Settings Manager, Simple CompizConfig Settings Manager, and Compiz Fusion Icon, you will need those to manage and configure compiz.  :P

---

