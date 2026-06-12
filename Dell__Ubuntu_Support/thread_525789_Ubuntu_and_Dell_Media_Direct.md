---
title: "Ubuntu and Dell Media Direct"
date: 2007-08-14
forum: Dell  Ubuntu Support
---

### Post by Matthew Wiebelhaus on 2007-08-14
I have a dell E1505 and want to reinstall  Dell MediaDirect on it along with ubuntu how would i go about doing it or is it even possible??

---

### Post by Rumplesmigskin on 2007-08-14
Ok, I'm not exactly sure what Dell MediaDirect is, although I assume it's some sort of media player. I guess you'd have to use wine (a linux implementation of the Win32 API, call it an emulator if you like although it isn't one) to get it to work. It's a shot in the dark though, a lot of programs don't work properly with wine, even when it's set up properly.

So that's a maybe bordering on a no.

Why exactly do you want MediaDirect anyway? There are loads and loads of native programs for doing that anyway, and the MediaDirect button on the laptop itself is set up to open the default audio player in Ubuntu.

---

### Post by Matthew Wiebelhaus on 2007-08-14
Dell Media Direct is pertty much a os

---

### Post by Rumplesmigskin on 2007-08-14
I'd probably resize the ubuntu partition then, by using GParted,and then reinstall MediaDirect from the CDs. 

For resizing the partitions, try booting from the Ubuntu CD, and then running GParted.

However, I don't know what it would do to the bootloader. If it screws with that, you might end up not being able to boot Ubuntu. I don't know for sure though. If it does mess with the bootloader, you can boot from your Ubuntu install CD and then re-install the GRUB. (GRand Unified Bootloader)

Hope this helps

---

### Post by mtbsoft on 2007-08-14
I've just recently seen a thread on this, apparently it IS possible so don't give up hope yet.  I'll try to track it down but I do recall it to be rather longwinded and quite complex.

---

### Post by Someone1 on 2007-09-21
I've just managed to do it (even with the live ubuntu cd, checkout that thread: [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)).

you start off with the dell media center cd which partitions your harddrive: about 50 mb at the beginning and 2 gigs at the end for the media center, you can choose whether to make one big partition out of the rest but as you want to install ubuntu you just give windows a part (like 15 gigs or whatever you want, just leave some for linux ;). then install windows on that partition. install dell media center in windows. REBOOT WITH DELL MEDIA CENTER! it needs to install some stuff of itself and if you got linux installed at that point it will fail... AFTERwards you can install ubuntu. note that the space you didnt use for windows isnt displayed as "free space" but something unknown iirc, just delete that empty partition and create your linux partitions. install it and everything works fine, even the media center startup-button.

---

### Post by semiconductor on 2008-05-13
I Just tried this and it didnt work. 
Media Direct gives me errors on instal in Vista. I think you need to start with the Media Direct CD and format the HD. Then install vista , then install the media Direct software in Vista. Then instal Ubuntu.
I cant be assed to go through all that again so ill do without it

---

### Post by Sunil Phani Manne on 2008-07-09
Hi,

I have solved the Media Direct problem by installing Ubuntu through Wubi. Install the Wubi by going to [http://wubi-installer.org/](http://wubi-installer.org/) and click on download and follow the instructions. Now I have Vista and Ubuntu and have the Media direct running fine with out any problems.

- Phani

---

### Post by Bossman74 on 2008-07-10
> **Sunil Phani Manne said:**
> Hi,

I have solved the Media Direct problem by installing Ubuntu through Wubi. Install the Wubi by going to [http://wubi-installer.org/](http://wubi-installer.org/) and click on download and follow the instructions. Now I have Vista and Ubuntu and have the Media direct running fine with out any problems.

- Phani

The only bad thing with this setup is that the installation is not permanent.  [https://wiki.ubuntu.com/LVPM](https://wiki.ubuntu.com/LVPM)

---

