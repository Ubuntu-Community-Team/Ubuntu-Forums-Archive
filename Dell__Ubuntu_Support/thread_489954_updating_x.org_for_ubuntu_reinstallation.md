---
title: "updating x.org for ubuntu reinstallation"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by dascheer on 2007-07-01
hey yall

a while ago ubuntu disappeared from my hard drive, so ive been trying to reinstall ubuntu.  currently i run kubuntu, which runs fine.

now i download the iso image (ubuntu 7.04 i386), booted from my cd-rom, and clicked the start and install ubuntu option.  then i go an error message telling me to get the latest version of x.org.  i went to wiki.x.org, looked around, and realized  that i have no idea what im doing.  

is it possible to get the lasted x update from synaptic package manager.  if so, what packages should i be looking for?

---

### Post by neptho on 2007-07-02
This is a rather strange error.  You had this error during installation, or while booted to the LiveCD itself?

---

### Post by dascheer on 2007-07-08
i can boot from the livecd fine, but i get the error message when i try to install

---

### Post by revilodraw on 2007-07-08
I have the exact same problem, and sadly, am currently using XP on an ancient laptop to rectify the problem..

Here's what happened for me;

Was running Edgy nicely, and had the ATI Radeon X1400 card working perfectly, and decided to do the upgrade to feisty, so downloaded the LiveCD...After burning the livecd, I got the blue screen saying i needed to update my x.org...whatever that is!

Screw that, i thought, restarted, and simply upgraded from Update Manager...

To my surprise, after installation, the same blue screen comes up, and when i cancel out of it there is no gui, but i do have a command line...

I'm sure lots of people must have had the same problem because the Dell Inspiron 6400 is very popular.

Any help??

---

### Post by dascheer on 2007-07-10
i think i figured it out.  the lastest version of x is gonna come out this august, which will have better support for beryl and compiz.  right now i dont think my laptop can handle either of those apps under ubuntu, so im prolly gonna have to wait.  right?

---

### Post by spud42 on 2007-07-10
i think i remember reading that you cant upgrade from dapper or edgy to fiesty. you may need to delete the original install and then install 7.04......

i have a dual boot xp/ubuntu  as work installed xp and it has to stay .i removed th ubuntu partition and started from scratch... installed no problem.

---

### Post by revilodraw on 2007-07-10
Let's say I did want to start from scratch, my Feisty LiveCD gives me the same problem ... Xorg is not configured correctly, no screens found... 

Curiously, when I 'sudo dpkg-reconfigure xerver-xorg' and change it to vesa, i get a different error message about signal 11?? This is really annoying me... I would have preferred to stay with Edgy which was working fine...

---

### Post by revilodraw on 2007-07-10
problem solved for me! i simply typed in 

"sudo aticonfig --force --initial" into the black command line and it worked..

If anyone with an X1400 wants my xorg.donf file i will happily send it...

---

