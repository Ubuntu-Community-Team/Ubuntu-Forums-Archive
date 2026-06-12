---
title: "optiplex 320 hardy install still fails on boot"
date: 2008-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ikman on 2008-06-11
I also have an Optiplex 320 (provided by my institution) with WinXP and attempted to dual boot Ubuntu 8.04. 

The only way I could even get the live CD to boot was to read the forums that with the suggestion to add pci=nomsi and then select with Fn-6 acpi=off nolapic and noapic. 

Once I got the live CD running I tried installing. No apparent problems until the reboot gave me only a black screen with a single letter (either b or f) and a couple green rectangles in addition to the underscore blinking cursor at the top of the screen.

I tried the forums again, which said to use the alternate CD and lilo. The alternate only gives the option for lilo if you do the advanced version (what's another 45 minutes?) and then when I rebooted after the install the boot hangs at:

[32.296191] system 00:09: iomem range 0xfee000...... could not be reserved
.. several iomem ranges could not be reserved ..
[32...    ] IO Window ..
.
.
[32...    ] Clocksource tsc unstable (delta -297862020706 ns)
[32....   ] Time: hpet clocksource has been installed.


So I checked more forums and found an ubuntu 7.04 fix that showed how to manually install lilo: 

"Please, check the following. It is for 7.04 but it provides detailed steps. http://ubuntuforums.org/showthread.php?t=409345"

which only had a couple problems. I used nano rather than vim and had to use aptitude rather than apt-get for some reason. Otherwise, it seemed to install lilo okay. I know I used the correct sda3 and so on because I checked it in the live CD instance. While I was at it, I did an 'update' and 'upgrade' as suggested in the forum. When I rebooted after doing liloconfig and lilo, I got a fullscreen Debian splash with a menu for my linux kernel, memtest, and WinXP, which I had edited in the fstab as directed, but the boot hung at the exact same place, i.e., right after the "Time: hpet clocksource has been installed" line.

The WinXP loaded okay. 

I'm all out of ideas but refuse to be defeated by a piece of silicon.

Any suggestions? 

Thanks

---

### Post by gnrathon on 2008-06-12
I have the very same crappy system
no matter what i do it never boots

The Ubuntu Team  should really look into this.

Grub will not work at all, im still not sure about lilo but by your post i dont think it will

The only boot loader left is super grub and grub 2
but i still dont know how to use these or install them

---

### Post by Rajvan on 2008-07-08
Ok, im starting to give up on this.

I am trying to boot(the installation is fine) ubuntu 8.04 on a optiplex 320, but I  get the same screen as ikman. A "b" and a 2 green rectangles. I've tried with Lilo, grub2, super grub, GAG and updating the bios on the optiplex (which actually made things worse.. before i didn't have to add the acpi=off parameter to boot the livecd.)

I'm at the end of the line here. Isn't there anything that can be done about this?

Edit: Ok, I finally got it working with this fix: [http://ubuntuforums.org/showthread.php?t=542546](http://ubuntuforums.org/showthread.php?t=542546). I followed it exactly, even the same partitioning.
I also had to add acpi=off to the grub2 boot parameter! (just press esc when grub loads and then "e" to edit the parameters.)

---

### Post by John Martin on 2009-01-15
Solution

Use kernel parameter:  hpet=disable
Change boot loader to: grub2

This works fine for me on 20 Dell Optiplex 320.
The best part is that everything works as supposed.

Best regards,
John Martin

---

### Post by flesh.wound on 2009-04-20
The problems with the Dell Optiplex 320 don't appear to be going away anytime soon.  Mine is a decommissioned box from work.  I was really excited about it.  Pentium D; hyperthreading; 64-bit; SATA.  I usually don't get hand-me-downs this good.

Well it isn't just Ubuntu this thing has trouble with.  It is problematic with Gentoo and FreeBSD as well.  I had better success with both of the latter but I'm wanting to run Ubuntu for specific commercial software support.

I will include my specifics in a later post after I get them documented.  I do have Ubuntu 8.10 AMD64 running on it now (sort of).  I'm having trouble with the ATI video which I believe will get solved easy enough tomorrow.  I'm dissatisfied with having to run LILO.  Not because I think LILO is bad but I just refuse to give up on GRUB.  GRUB could mount the drive and read from it so I'm sure there has to be a workaround for booting it properly.  My ultimate solution so far centers around "acpi=off" which alone got me past the hanging during boot of the CD.  The CD also gave me troubles during the install either because of the drive itself or the PATA support.  The CD was fine.  I ended up booting to a USB flash and doing the install from that.

I feel like I can get everything resolved but am unsure about working around the ACPI issue.  By doing "acpi=off" it disables the hyperthreading which is extremely undesirable.  Who wants to run on half of a CPU?

More to come...

---

### Post by dafut on 2009-11-21
If you're having trouble getting the kernel to load on boot up, you might try rearranging your BIOS to boot first order to a USB device, then build your /boot partition on a small USB drive. 

I'd attempted to install Linux distro's on a Optiplex 320 at least a dozen different times and ways, all of them failing. I could get to Grub, but not beyond. I could load a LiveCD or SysRescue, but never from either a SATA or PATA drive. Once I put my /boot partition on the thumb drive, I was able to install Ubuntu Karmic Server without a problem. If I remember correctly, the one thing I had to do at install was, "linux noacpi".

---

### Post by imadera on 2010-02-07
Hi There!

I have two days working to solve this issue and finally I have got Ubuntu Linux 8.04.4-LTS running at a DELL Optiplex 320.  The procedure to did it is as follows:

[1]
I did use the CD to install Ubuntu Linux Server Edition (ULSE) 8.04.4-LTS.

[2]
I selected the INSTALL UBUNTU SERVER and PRESSED [F6] Advanced Options at the Boot Menu from the CD and I did edit the line of parameters that are passed to the kernel, as follows:

- I deleted the `quiet` option, and
- I added the: `hpet=disable` option, before the `--` that ends the line of parameters. 
- I selected the EXPERT MODE in the [F6] Menu for allowing me to choose the boot loader at the end of the installation procedure.

Once I did these changes, I pressed ENTER for starting the INSTALL PROCEDURE.

[3]
I did install the ULSE following the standard steps and according to my needs, AND AT THE FINAL STEPS OF THE INSTALLATION, I did choose the INSTALL LILO AS THE BOOT LOADER.

[4]
After installing LILO as the Boot Loader, I did FINISH THE INSTALLATION and I did reboot the server, but KEEPING THE CD AT THE TRAY, for booting from CD at RESCUE MODE, in order to EDIT THE `/etc/lilo.conf` for LILO to pass the `hpet=disable` parameter to the kernel, as I will describe in the next steps.

[5]
Instead of booting ULSE from the Hard Disk for the first time, you need to BOOT FROM CD and SELECT RESCUE MODE and passing the `hpet=disable` to the KERNEL again, in order to the Rescue Mode to boot properly.

[6]
Once the Rescue Mode starts, you just have to follow the instructions until the Rescue Mode asks you to decide to MOUNT YOUR ROOT PARTITION (i.e.: "Mount /dev/sda1/ as the root partition").  This will allow you to mount `/` and then run a shell on `/` to edit the `/etc/lilo.conf`.

[7]
Once you had mounted `/dev/sda1` (or the corresponding to your hardware) to the root partition `/`, the Rescue Mode will allow you to select "RUN SHELL AT ROOT PARTITION".  You have to select this option and then a SHELL will appear at the bottom of your screen.

[8]
In the SHELL, simply edit the `/etc/lilo.conf` by using vim, this can be done with: `vim /etc/lilo.conf`.  Inside the Vim Editor, you can move using the `:112` command for going to the exact line of text where you have to edit the file.

[9]
One in the LINE # 112 of the `/etc/lilo.conf` file you should be at the `append = "root=/dev/sda1  "` option where the kernel parameters are defined.  Simply use the `A` (upper cased A) to go to the end of that line and INCLUDE the `hpet=disable` option inside the doble quotes.  The line (after edited) should appear as:

append = "root=/dev/sda1  hpet=disable "

Once edited, simply exit the Vim editor with ESC and then `:wq!` for writing the changes.  YOU HAVE TO FOLLOW THE STEP # [10].. PLEASE READ:

[10]
Once you had edited the LILO.CONF file, YOU MUST EXECTUTE `lilo` at the SHELL, simply writing `lilo` and pressing ENTER.  This will prepare LILO to include your changes to the Boot Loading Process.

[11]
Exit from the shell with `exit` and you will be at the Rescue Mode again.  There you should select REBOOT or RESTART and then the boot process will start.  Your DELL Optiplex 320 should BOOT Ubuntu Linux Server 8.04.4-LTS without problems.

I hope this information be helpful for those people that need it.

Good luck.

Igor.

---

### Post by jig36 on 2011-01-19
this system has issues with grub and is fixed with grub 2 9.10  Karmic Koala, 10.04 LTS Lucid Lynx,10.10 Maverick Meerkat, 11.04 Natty Narwhal should work fine with fresh install with on this machine

---

