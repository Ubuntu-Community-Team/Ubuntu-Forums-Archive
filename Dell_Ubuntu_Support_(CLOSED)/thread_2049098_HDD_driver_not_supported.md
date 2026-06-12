---
title: "HDD driver not supported?"
date: 2012-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by csytk on 2012-08-27
I recently got a Dell Inspiron Special Edition 7720 computer.   I am trying to install Ubuntu along side Windows.  When I use the WUBI  installer, the installation of Ubuntu works as long as I do not boot  into Windows; if I boot into Windows, when I go back into Ubuntu, I am  given a variety of error messages which claim to have corrupt or missing  kernel/root directory, etc.  I have been working with this problem for  about a week, and have reinstalled Ubuntu MANY times.  So far, I have  eliminated all of the following problems:  Corrupt WUBI installation  (Downloaded multiple times, used on other systems), I have tried using a  CD and a flash drive, both of which work on other computers.  I know  that no program within Ubuntu is creating the problem.  I know that  others have successfully installed Ubuntu on a computer with my  operating system (Windows 7 SP1).


  I have already posted on askubuntu, where nobody had a  solution.  I have talked to a friend who is completely baffled, and have absolutely no idea myself.  When I spoke with the Dell service technician who came over  today to replace my keyboard, he suggested that the driver for my HDD  was so new that it was not compatible with the current version of  Ubuntu.  His reasoning is as follows:
  1) During an install from a flash drive or CD, where I am supposed to  get the option to wipe my system or create a dual boot, I get a window  that asks me to select a hard drive partition, but none are listed.
2) This model of computer was made public in June of this year, while Ubuntu was released in April
  Adopting this theory, it would seem to me that the WUBI install fails  after booting into Windows because Ubuntu can no longer find the files  that it needs to load.


  Does this theory seem at all plausible to anyone?  I just want to  install Ubuntu and have it stay on my computer.  I don't care how I put  it there, I just need it to work, so I would TRULY appreciate any advice  or suggestions anyone could give.
  Thanks so much for your time and support!!!


***When installing from a flash drive on any other device, I have at some point gotten the screen shown in the first picture (Normal Install).  On this particular laptop, however, I get the second picture (My Install) instead.  When I connect our external USB HDD during the install process, I get the "normal" window, followed by the third picture (My Install with External HDD).

---

### Post by andrew s 123 on 2012-09-19
Hi,

I've got the same laptop and have run into similar problems.  Wubi installer works (Ubuntu 12.04) but then when I run Windows 7 it corrupts the Ubuntu installation.  I tried to use the Ubuntu 12.04 CD to install, but similar to you the installer can't see the hard drive.  I stopped at that point because I didn't want to wipe out the Windows 7 installation.

Did you find any resolution to this?

One thing I am wondering about is the HDD configuration.  There is a 32 GB SSD cache in my configuration, used with some kind of Intel tech to enable a rapid reboot.  It's a pretty new type of hardware feature so I wonder if it is tripping up the installers and/or boot loaders?

---

### Post by oldfred on 2012-09-19
Is it like one of these?

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by csytk on 2012-09-19
Good morning.  I apologize for not posting a solution, I actually posted on a few forums because I was really having trouble finding a solution, and I forgot to update this one.  So, here's the thing:  I still don't entirely understand the  problem, but my understanding is that some form of the RAID configuration which the 32gb mSATA card employs by default is preventing GRUB from finding the HDD and SSD.  Therefore, if you install to one of your disks, when you restart, the files are labeled as missing or corrupt.  I was able to resolve this issue, but not with WUBI.  What I had to do was boot into a live session (trial mode) using the CD or flash drive (for the full version of Ubuntu, rather than WUBI).  Then, I opened terminal, and removed the  RAID configuration.  Unfortunately, I have not found a solution that supports RAID.  For more information about that, see the chosen answer on this post: 
[http://askubuntu.com/questions/141656/ubuntu-12-04-does-not-see-windows-already-install-on-my-computer-dual-installat](http://askubuntu.com/questions/141656/ubuntu-12-04-does-not-see-windows-already-install-on-my-computer-dual-installat)
and the link it contains, also accessible here:
[http://askubuntu.com/questions/21267/why-doesnt-the-installer-see-all-of-my-hard-drives](http://askubuntu.com/questions/21267/why-doesnt-the-installer-see-all-of-my-hard-drives)

After you remove RAID, you should be able to click the install button on the desktop of the live session and proceed with the install as normal.  Note that if information or Windows is stored on the SSD, it may not function properly when you boot back into windows, depending on how it is configured, so you should probably back it up before hand. 

Let me know if this works for you, or if you find a better solution.

---

