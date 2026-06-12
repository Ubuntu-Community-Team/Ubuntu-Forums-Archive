---
title: "Dell inspiron 1150 wont boot"
date: 2010-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pckid on 2010-05-03
hi
installed ubuntu 10.04 on a dell inspiron 1150. it gets to the  purple boot screen then when it should be at the login the screen goes black and the keyboard/mouse go dead. You can still hear all the disks spinning and stuff. Can someone help?!?!?!?!

specs:

ubuntu 10.04 LTS
40 gb hdd
512mb ram
intel 850 extreme graphics (i think)
intel centrino cpu 2.80 ghz

---

### Post by quixote on 2010-05-04
That sounds like a graphics driver problem.  (Or, just possibly, it runs out of memory??  512MB sounds pretty small for a fast CPU and high-end graphics?)  

Boot with a livecd and find out which is your exact graphics model by opening a terminal (Applications > Accessories > Terminal) and typing ```
lspci | grep 'VGA'
```(It's case sensitive.)  Then try searching for that model and lucid, eg "Intel nnnn Lucid Ubuntu" (without quotes).

---

### Post by pckid on 2010-05-05
im pretty sure its not a graphics driver because the caps lock buttons and all the other ones that light up wont.

---

### Post by franck31 on 2010-05-06
Same problem here with the same specs. It is working fine with 9.10 but when I tried to upgrade it just won't boot. I also tried the livecd and same effect.

I tried to look at what is happening during boot by pressing escape.
There is a message about "firmware not found", then another line and then a lot of color squares then it goes dead.

---

### Post by pckid on 2010-05-06
exact same problem. its running ubuntu 9.10 now. i installed ubuntu tweak and it said my processor is i686. is that 64 bit? does that have anything to do with it?

---

### Post by quixote on 2010-05-07
i686 can be 32-bit or 64-bit depending on the age of the computer.  No, it doesn't have anything to do with the failure to boot.  (Or maybe I should say I don't see how it could.)  To see whether your system is 64-bit type in a terminal (Applications > Accessories > Terminal):```
uname -a
```If the line it gives you has x86_64 toward the end, it's 64-bit.  Otherwise, it's 32-bit.

Unfortunately, we're no closer to figuring out what the actual problem is.  But if it's working in 9.10, and you've got that back on your system, I guess the most practical thing to do is quit there.  :-?

---

### Post by franck31 on 2010-05-07
It looks like the reason is explained here 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9240296](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9240296)

10.04 with kernel 2.6.32 does not support the Intel 852 graphic controler.

A workaround is described in the link.

---

### Post by franck31 on 2010-05-07
I confirm that the workaround is working. I now have an Inspiron 1150 with 10.04.

---

### Post by pckid on 2010-05-07
which work-around do i use? and do i just upgrade from 9.10 or do i have to do a complete re-install?

---

### Post by pckid on 2010-05-07
it has a whole bunch of files to download. which one should i get? and what version of ubuntu is this?

---

### Post by pckid on 2010-05-07
i have just confirmed that it is intel 855gm graphics.


lspci | grep 'VGA'
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

---

### Post by quixote on 2010-05-07
The link is about installing the next kernel up, so it's a new *kernel*.  Same version of ubuntu as you're using, i.e. Lucid.  The newer kernel fixes the bug which prevents the OS from understanding the graphics card.

The [instructions in French]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9236684&postcount=6") (just above the linked comment) tell you the header and image files to download.  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/) has six files, two for 64-bit machines (the ones with amd64 in the name) and two for 32-bit (the ones with i686).  You need both files relevant to your architecture plus the one with "all" in the name.  I'm not sure if you need the "source" or not, but get it while you're at it.  If the system ever needs to compile a new kernel module, I think it'll need it.  Put them somewhere that you will be able to access when trying to fix Lucid: USB, CD, or on the drive itself if you can access recovery mode.

The French instructions suggest a reinstall using an alternate-install CD, and installing using text mode (step 4).  Then step 5 is to install the three new files needed for the new kernel.  If you can get into recovery mode on your machine, you don't need to reinstall.  You can just run step 5 from the command line.  

**Except**: you don't need sudo, because you're already root.  And I would suggest using the full filename, just to make sure you don't install any old packages you don't want that happen to be around! 

So the commands would look like this:```
dpkg -i /path/to/linux-headers-2.6.33-02063303-generic_2.6.33-02063303_i386.deb
[I](e.g. if they're on USB: /media/some-UUID or maybe /media/disk-1
if they're in your home dir: /home/your-login-name)[/I]
dpkg -i /path/to/linux-headers-2.6.33-02063303_2.6.33-02063303_all.deb
dpkg -i /path/to/linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb
dpkg -i /path/to/linux-source-2.6.33_2.6.33-02063303_all.deb
```When entering commands, remember than you can use tab-complete: type the first few letters then hit tab and it'll complete as much as it can until the next ambiguous point (if there is one) which you then fill in and hit tab again.

Step 7 about installing ubuntu-desktop is only necessary if you've used the alternate-install CD to make a new installation.  Otherwise you already have that.

Then, says, the poster, "Reboot and everything works."

I hope so! :D

---

### Post by pckid on 2010-05-07
im no noobie with kernels. im just bad with video cards. will this be the default kernel when i boot or do i need to enter the grub booter thing?

---

### Post by pckid on 2010-05-07
can i change the names of the kernel .deb files so that they are easier to type in?

---

### Post by quixote on 2010-05-07
Personally, I wouldn't change the names, but then I'm somewhat risk-averse. :)  To make it the default kernel, I'm not sure with grub2 how it will work.  Running sudo update-grub will find and include all linux kernels on your system.  I think it will be the default, because it's the most recent, but I'm not sure.  If it's not, it might take a bit of [editing config files]("https://help.ubuntu.com/community/Grub2").  (Sorry that I went into excess detail in the last comment.  I never know which side to err on.)

---

### Post by pckid on 2010-05-08
guys, im making a patched disk using reconstuctor. i will leave the link when i finish.

---

### Post by pckid on 2010-05-11
the reconstructed disk was corrupted and reconstructor wouldn't let me download a new one, so i just gave up and put ubuntu studio 9.10 on it.

---

### Post by quixote on 2010-05-12
Well, I guess this is a "fail" for fixing it, but you managed to cure it. :D  Good to know.

---

### Post by wrwetzel on 2010-07-23
I had the exact same problem with an 1150 as reported here and similar to reports for other machines in other threads. Since this thread has the Inspiron 1150 specifically mentioned in the topic I'm posting the solution that worked for me here, which I distilled from the other threads.

My 1150 has an Intel 852GM /GME / GMV video chip.

------------------
Installation

During installation press <Space> when two small icons (one may have a stick-figure shape) appear at the bottom of the screen. This will take you to the boot menu.

Press <Tab> or <F6> to edit the kernel boot options. When booting from a CD I had to use <F6>, from a thumb drive I had to use <Tab>, not sure why the difference. I had to press <esc> to dismiss the menu that popped up when I pressed <F6>. From the thumb drive I also got an annoying echo of the boot command with every character typed but it worked fine.

Position the cursor just to the left of the "--" at the end of the line, if not already there.

Add:

**i915.modeset=1**

to the boot options. I also removed (by backspacing) 
[B]
quiet splash[/B]

so I could follow the boot progress. The above solves the problem for the kernel running during installation but does nothing for subsequent boots of the installed kernel.

---------------------------
First Boot of Installed Kernel:

Get to the Grub menu by pressing <Shift> as soon as the boot starts. This is immediately after the BIOS messages disappear.

Press <e> to edit the boot line.
Position the cursor after "quiet splash" and add the same option as above:
[B]
   i915.modeset=1[/B]

Then press <Ctrl-x> to boot.

This solves the problem but is a nuisance to do every time. That can be fixed by adding a configuration file.

-------------------
Subsequent Boots

Create the following file with your favorite editor:
[B]
/etc/modprobe.d/i915.kms.conf[/B]

containing the following single line:

[B]options i915 modeset=1
[/B]
-------------------

My Dell Inspiron 1150 is now running Ubuntu 10.04 just fine. BTW, KMS stands for "Kernel Mode Settings", a facility to move video setting out of xorg.conf into the kernel. This change enables KMS.

Summary:

Kernel option during boot: **i915.modeset=1**
Permanent: **option i915 modeset=1** -> **/etc/modprobe.d/i915.kms.conf**


Hope this helps,
Bill Wetzel

---

### Post by SpEcIeS on 2010-08-19
To fix the Intel 855gm graphics use the following:

```

sudo add-apt-repository ppa:glasen/intel-driver
sudo add-apt-repository ppa:glasen/855gm-fix

```

Upgrade the Intel graphic drivers and add the following packages:

```
sudo apt-get install dkms 855gm-fix-dkms
```

reboot

Good luck :)

---

### Post by jotathebest on 2011-04-17
Thank you very much!!! your solution was the best way to install ubuntu in my lap-top

It really works!! thank you so much :)

> **wrwetzel said:**
> I had the exact same problem with an 1150 as reported here and similar to reports for other machines in other threads. Since this thread has the Inspiron 1150 specifically mentioned in the topic I'm posting the solution that worked for me here, which I distilled from the other threads.

My 1150 has an Intel 852GM /GME / GMV video chip.

------------------
Installation

During installation press <Space> when two small icons (one may have a stick-figure shape) appear at the bottom of the screen. This will take you to the boot menu.

Press <Tab> or <F6> to edit the kernel boot options. When booting from a CD I had to use <F6>, from a thumb drive I had to use <Tab>, not sure why the difference. I had to press <esc> to dismiss the menu that popped up when I pressed <F6>. From the thumb drive I also got an annoying echo of the boot command with every character typed but it worked fine.

Position the cursor just to the left of the "--" at the end of the line, if not already there.

Add:

**i915.modeset=1**

to the boot options. I also removed (by backspacing) 
[B]
quiet splash[/B]

so I could follow the boot progress. The above solves the problem for the kernel running during installation but does nothing for subsequent boots of the installed kernel.

---------------------------
First Boot of Installed Kernel:

Get to the Grub menu by pressing <Shift> as soon as the boot starts. This is immediately after the BIOS messages disappear.

Press <e> to edit the boot line.
Position the cursor after "quiet splash" and add the same option as above:
[B]
   i915.modeset=1[/B]

Then press <Ctrl-x> to boot.

This solves the problem but is a nuisance to do every time. That can be fixed by adding a configuration file.

-------------------
Subsequent Boots

Create the following file with your favorite editor:
[B]
/etc/modprobe.d/i915.kms.conf[/B]

containing the following single line:

[B]options i915 modeset=1
[/B]
-------------------

My Dell Inspiron 1150 is now running Ubuntu 10.04 just fine. BTW, KMS stands for "Kernel Mode Settings", a facility to move video setting out of xorg.conf into the kernel. This change enables KMS.

Summary:

Kernel option during boot: **i915.modeset=1**
Permanent: **option i915 modeset=1** -> **/etc/modprobe.d/i915.kms.conf**


Hope this helps,
Bill Wetzel

---

