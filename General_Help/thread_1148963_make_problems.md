---
title: "make problems"
date: 2009-05-04
forum: General Help
---

### Post by sir_nasty on 2009-05-04
Hey all, I'm a relative noob so bear with me....  Trying to do a simple make, I've loaded the proper linux-headers and a few other thigns.  Fails with 


*** No rule to make target 'arch/x86/kernel/asm-offsets.c', needed by 'arch/x86/kernel/asm-offsets.s'. Stop.


Found a page saying it's a bug.... I have a new dell mini 9, hardy heron running on the 2.6.24-22.lpia kernel....

any ideas or workarounds?

---

### Post by sir_nasty on 2009-05-04
if I can't solve this issue then solving my ./configure problem might help...

that one says "Error:  kernel-sources cannot be found!"

---

### Post by Locutus_of_Borg on 2009-05-04
you will need the full kernel source, and to be in the root source directory, and be root

something like this will download, and compile the 2.6.29 kernel tree:
```

sudo -i
cd /usr/src/
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.29.tar.gz
tar xzf linux-2.6.29.tar.gz
cd linux-2.6.29
cp ../linux/.config .
make oldconfig
make && make modules_install
cp arch/x86/boot/bzImage /boot/NEW_KERNEL

```

be sure to change grub to boot new kernel, and its a good idea, if you are going to use the new kernel primarily, to change the linux symlink to point to the new source
```

sudo rm /usr/src/linux && sudo ln -s /usr/src/linux-2.6.29 /usr/src/linux

```

---

### Post by sir_nasty on 2009-05-04
so I can run/install this new kernel then boot to it once and run the make that I need to then just boot off/use the old kernel?  

I like the lpia kernel simply because it helps the battery life of my mini...

---

### Post by snowpine on 2009-05-05
I don't think you can install a kernel that uses a different architecture than your install (just like you wouln't use a 64 bit kernel with a 32 bit install)... you'd need to find an lpia version of whatever it is you're trying to install (which can be difficult).

---

### Post by sir_nasty on 2009-05-05
unfortunately there is no updated version of the lpia kernel... so I'm running the install/make of the above mentioned one and crossing my fingers....  If I can't do it then that fricken make bug in kernel versions under 2.6.27 is going to hose me...

fricken usb adsl modem.....

---

### Post by snowpine on 2009-05-05
Sure there is; I am running Jaunty with 2.6.28-11-lpia on my Mini 9.

[https://launchpad.net/ubuntu/jaunty/lpia/linux-lpia/2.6.28.11.15](https://launchpad.net/ubuntu/jaunty/lpia/linux-lpia/2.6.28.11.15)

No idea if it will work with the factory Dellbuntu 8.04; I did a fresh install.
(ps I have tested both i386 and lpia and there is no difference in battery life; if you are considering a fresh install at any point, my advice is go with the i386 for greater compatibility.)

---

### Post by sir_nasty on 2009-05-05
strange... when looking at the kernel images in synaptec it wouldn't show me that version....


I'm sure this has been hashed all over the place but why jaunty over hardy heron?

---

### Post by snowpine on 2009-05-05
You can't install the newer kernel through Synaptic.

I was disappointed with Jaunty lpia on my mini 9. I would recommend the "regular" i386 version over lpia (if you ever decide to install Jaunty). If Hardy meets your needs, there is no reason to install something newer--Hardy is the current long term support version (supported through April 2011) and the special version you are running is custom tailored for your mini 9 hardware.

---

### Post by danwood76 on 2009-05-05
@sir_nasty

You dont need the entire kernel sources just the headers, these should be available through synaptic.
What are you trying to compile?

Normally to get everything you need you can use apt like this:
```

sudo apt-get build-dep PROGRAM_NAME

```

---

### Post by sir_nasty on 2009-05-05
providing that I can get this stupid eagle-usb driver to install I will have no need to change otherwise I'm going to be upset....


I bought this stupid usb dsl modem just for testing stuff onsite and I just need it to give me line statistics, mainly SNR....

---

### Post by sir_nasty on 2009-05-05
now backing up just one second I got the modem working, the eagle-atm drivers are included in the 8.04 release and it functions fine.  However, I need the eagle-atm-usb diagnostic tools to work.  mainly eaglestat and eaglediag, in order to get those working it calls /proc/driver/eaglestat and to install that I believe I need to compile/make the eagle-usb driver.

The reason I want those is so that I can get the statistics I need...

---

### Post by sir_nasty on 2009-05-05
well still not working... and it's making me mad... kind of at a loss now... I'm starting to guess that since all these files/packages are for an i386 architecture perhaps if I move to jaunty i386 it will work...

anyone else got insight?  I'm encountering the same issues while running the 2.6.29 kernel...

---

### Post by sir_nasty on 2009-05-05
For anyone who needs this I FINALLY got the info I needed...stumbled accross this page, followed one of the links at the top, saved the file as stats, run it and I have all the diagnostic info I need!

[http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmControl](http://atm.eagle-usb.org/wakka.php?wiki=UeagleAtmControl)

Thanks to all for the replies!

---

