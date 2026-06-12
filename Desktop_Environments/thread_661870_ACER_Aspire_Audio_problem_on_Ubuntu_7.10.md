---
title: "ACER Aspire Audio problem on Ubuntu 7.10"
date: 2008-01-08
forum: Desktop Environments
---

### Post by YuXu on 2008-01-08
Hi everyone,
I have just bought the Acer Aspire 5710, unlike my old PC there is no sound in this one,  on Ubuntu 7.10.
I can't solve my audio problem myself. Do you know what is the problem?
Thanks for your help before.

---

### Post by codesplice on 2008-01-08
What audio card do you have?

I had to do a few different things to the get audio working on my hp dv6700 with a Realtek ALC268. If you have a similar card, the following might be helpfull:

> The Realtek ALC268 audio device is not supported by the version of ALSA (1.0.14) that came with Daryna/Gutsy. You will need to manually install version 1.0.15. You can do this easily via "sudo apt-get install linux-backports-modules" (followed by a reboot), or manually by downloading alsa-lib-1.0.15.tar.bz2 from the ALSA project. Extract the tarball, "cd" to that directory, "./configure", "make", and "sudo make install". Do the same for alsa-driver-1.0.15.tar.bz2. Then "sudo depmod -a" and reboot. Sound should now work :)

---

### Post by dabang on 2008-01-08
If I get it right, this laptop has an Intel HDA soundcard? If so, double click on the little speaker icon at the upper right of your Gnome desktop and the mixer will open. Go to “Edit -> Configure” and check “Surround”. Now turn up the "Surround" volume in the mixer and it should work! At least it did for my Acer Aspire 5572.

---

### Post by magnat2 on 2008-01-09
Go to [http://acer5720linuxubuntu.blogspot.com/](http://acer5720linuxubuntu.blogspot.com/)   there is an how to for aspire 5720 that as the same sound card as you, and many things more, wireless, etc...

Good luck! Dont forget to comment!

---

### Post by deepaknr on 2008-01-12
I have Acer Aspire 5710G notepad. I has issues with sound configuration. Sound was not at all coming out...

I did this, hope it might help. Firstly I updated the ALSA drivers, what ever ubuntu 7.10 has and then edited this file

$ sudo gedit / etc / modprobe.d / alsa-base

at the end of the script, i added this

options snd-hda-intel model = toshiba

Rebooting should make the sound work. For some reason toshiba should be acer, but if you make it as acer, it never worked for me.

---

