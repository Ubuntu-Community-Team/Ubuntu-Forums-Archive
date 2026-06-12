---
title: "How can i install my sound drivers?"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Rackerz on 2005-11-17
I want to install my Realtek AC97 sound drivers as my sound is terrible. 

The package is called 'realtek-linux-audiopack-3.5-1.tar.bz2' Hope this is enough information.

Thanks!

---

### Post by sdr_ar on 2005-11-17
Hi! you have two ways

the first is automatic:

execute

  ./install

The other is manual 

These are the steps:

1) tar -xjvf realtek-linux-audiopack-3.5-1.tar.bz2
2) Complied source code
	a. cd alsa-driver-1.0.9b_1.
	b. ./configure
	c. make
	d. make install
	e. ./snddevices
3)Edit your /etc/modules.conf

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
	       snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
        # ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

4) Reboot your machine
5) open alsa mixer from the terminal, and disable mute

This is taken from the readme file that comes with the driver. It worked very well for me.

Regards

---

### Post by Rackerz on 2005-11-17
Well all seems to go well up until ./configure;


rackerz@WORKGROUP:~/Desktop$ tar -xjvf realtek-linux-audiopack-3.5-1.tar.bz2
./realtek-linux-audiopack-3.5-1/
./realtek-linux-audiopack-3.5-1/test.wav.bz2
./realtek-linux-audiopack-3.5-1/alsa-driver-1.0.9b_21.tar.bz2
./realtek-linux-audiopack-3.5-1/alsa-utils-1.0.9a.tar.bz2
..... (it basically extracts everything else.
rackerz@WORKGROUP:~/Desktop/realtek-linux-audiopack-3.5-1$ ./configure
bash: ./configure: No such file or directory
rackerz@WORKGROUP:~/Desktop/realtek-linux-audiopack-3.5-1$ cd ./alsa-driver-1.0.9b_21/
rackerz@WORKGROUP:~/Desktop/realtek-linux-audiopack-3.5-1/alsa-driver-1.0.9b_21$
./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
rackerz@WORKGROUP:~/Desktop/realtek-linux-audiopack-3.5-1/alsa-driver-1.0.9b_21$

So any idea on why it says that?

Thanks

---

### Post by sdr_ar on 2005-11-17
Do you have installed buil-essentials?
If not, do this in the terminal:

:$ sudo apt-get install buil-essentials


With this command it will be installed the GCC Compilator.
Then try again ./configure

---

### Post by sdr_ar on 2005-11-17
sorry, it is build-essentials

:$ sudo apt-get install build-essentials

---

### Post by Rackerz on 2005-11-17
rackerz@WORKGROUP:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials
rackerz@WORKGROUP:~$

Looks like it didn't work, or did it work?

---

### Post by sdr_ar on 2005-11-17
The correct package name is build-essential.
Try it, and tell me.

---

### Post by David Valentine on 2005-11-22
I'm a Linux newbie attempting to set up Ubuntu 5.10 on an AMD 64 system (MSI MS-7145 Mobo with RS480 + SB400 chipset, Realtek ALC655).  I followed your automatic instructions above, and found that I also needed to install libncurses5.dev for compiling to complete.  After compiling, it attempted to find my sound card (which is built-in), but failed and exited.  I'll try the manual install tomorrow, but the Readme.txt file says > Step 2. Turn on sound support (soundcore module, default turn on) What is that referencing?  Thanks for your help!

---

### Post by sdr_ar on 2005-11-22
I think that sound support is already turned on. 

Try modinfo soundcore in the terminal and see what it says

Then try installing it manually

---

### Post by David Valentine on 2005-11-22
[QUOTE=sdr_ar]Try modinfo soundcore in the terminal and see what it says[/QUOTE]It says> filename:       /lib/modules/2.6.12-9-amd64-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E11490DC3F523551C4C2A6D
depends:
vermagic:       2.6.12-9-amd64-generic gcc-3.4
I'm a little embarrassed because I had not enabled AC97 in the BIOS; after I did, however, the auto install was still unable to find my sound system.  I'll try the manual install method now.

---

### Post by David Valentine on 2005-11-22
Manual install failed as well.  It executed ./configure fine, but it returned errors when I ran make and make install.  I tried it both without and with sudo.

Should I just come back to the AMD64 version of Ubuntu once all the new hardware kinks have been worked out?  

Thanks again for your help.

---

### Post by David Valentine on 2005-11-22
Go figure...just as I'm about to throw in the towel, sound starts working at the next restart.  And I don't know why.

---

### Post by sdr_ar on 2005-11-23
Linux's things. 
Summary:
You have activated AC97 in your BIOS, and then it worked (magicly or not).
Does it work everytime now?

---

### Post by David Valentine on 2005-11-30
Yes, it's rock solid now.  I'm guessing that it was because of the BIOS change, but it's odd that the success magically came a few reboots later.  Thanks for following up.

---

### Post by Rackerz on 2005-12-05
Am i supposed to get these errors? 

9b_22# make install
find: /root/realtek-linux-audiopack-3.5-1a: No such file or directory
find: /root/realtek-linux-audiopack-3.5-1a/alsa-driver-1.0.9b_22: No such file o
r directory
find: /root/realtek-linux-audiopack-3.5-1a: No such file or directory
find: /root/realtek-linux-audiopack-3.5-1a/alsa-driver-1.0.9b_22: No such file o
r directory
find: /root/realtek-linux-audiopack-3.5-1a: No such file or directory
find: /root/realtek-linux-audiopack-3.5-1a/alsa-driver-1.0.9b_22: No such file o
r directory
find /lib/modules/2.6.9-1.667smp/kernel/sound -name 'snd*.*o' | xargs rm -f
find: /lib/modules/2.6.9-1.667smp/kernel: No such file or directory
make[1]: Entering directory `/home/darren/Desktop/realtek-linux-audiopack-3.5-2/
alsa-driver-1.0.9b_22/acore'
Makefile:5: /root/realtek-linux-audiopack-3.5-1a/alsa-driver-1.0.9b_22/toplevel.
config: No such file or directory
Makefile:6: /root/realtek-linux-audiopack-3.5-1a/alsa-driver-1.0.9b_22/Makefile.
conf: No such file or directory
Makefile:11: /root/realtek-linux-audiopack-3.5-1a/alsa-driver-1.0.9b_22/alsa-ker
nel/core/Makefile: No such file or directory
Makefile:19: /root/realtek-linux-audiopack-3.5-1a/alsa-driver-1.0.9b_22/Rules.ma
ke: No such file or directory
make[1]: *** No rule to make target `/root/realtek-linux-audiopack-3.5-1a/alsa-d
river-1.0.9b_22/Rules.make'.  Stop.
make[1]: Leaving directory `/home/darren/Desktop/realtek-linux-audiopack-3.5-2/a
lsa-driver-1.0.9b_22/acore'
make: *** [install-modules] Error 1

Basically, it's the Error 1 errors I'm talking about.

---

### Post by sdr_ar on 2005-12-09
Try running make install with sudo, not with root. Because as I can see, it is looking for some files in the root directory, and you have all the files for installation in /home/darren/Desktop/realtek-linux-audiopack-3.5-2
I don't find any other error.

---

### Post by OldManRiver on 2007-12-05
All,

Having this problem on my ECS 755-A MB with Ubuntu 7.10.  Followed this thread and the debugging thread at:

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

This thread helped me find the realtek-linux-audiopack-4.07a driver file I needed, but when I run the > ./installthe install gets to the configuration parts and always aborts when writing the config file.  I tried using the manual install running the > ./configure command and get the "no such command or file" error.

I ran the "alsa-info.sh" script twice, once before starting with PB at:

[http://pastebin.ca/811080](http://pastebin.ca/811080)

and then again after the install ran with PB at:

[http://pastebin.ca/805573](http://pastebin.ca/805573).

You can see the difference made, but still no audio.  Need some help here.  Also step-by-step through the debugging at:

[http://pastebin.ca/808756](http://pastebin.ca/808756).

Also went to IRC to see if I could get help, only one response there.

Thanks!

OMR

---

### Post by OldManRiver on 2007-12-07
All,

I know I added to an old thread, but need help all the same!

OMR

---

### Post by OldManRiver on 2007-12-12
Why is it so hard to get help on sound?

---

