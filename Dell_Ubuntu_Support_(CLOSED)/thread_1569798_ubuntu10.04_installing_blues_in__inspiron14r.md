---
title: "ubuntu10.04 installing blues in  inspiron14r"
date: 2010-09-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by saiki4116 on 2010-09-07
i have dell inspiron 14r with partitions as follows
1.c drive with 158gb
2.s drive for data with 90gb
3.e drive(i made a drive for future installation of linux)
so, i got ubuntu 10.04 livecd
started installing as follows
i went for advanced partioning,then changed file system of the 50 gb drive to ext4 type,and changed mountpoint as '\',with format option included
then didnt change any advanced options.
after that it was installed and instructed me to restart.
when i have restarted,it showed a blank screen..so i pressed power button
after i started it again..
then i got boot menu showing ubuntu and windows loaders.i logged onto ubuntu and found out that wifi device and ati drivers are not detected and scroll for touchpad is not working..i restarted and loaded windows7.
now when i restarted it is showing no OS is present..then i again installed linux,when login into windows and logout,same prob occured.....
so,i formatted whole disk and restored factory image.this time i installed ubuntu using WUBI in a drive with size of 20gb,not in c drive.now wifi,ati device drivers are not detected..touchpad scroll is also not working...
can anyone tellme why OS is not detected for normal installation...and give me link to download wifi drivers(broadcom)and procedure to install it..
What will be the difference in performance by installing ubuntu by livecd and by WUBI?
NOTE:wifi worked when i clicked 'try ububtu 10.04' in live cd installer menu

---

### Post by quixote on 2010-09-09
Bootloaders are tiny operating systems that tell the machine where to find the real operating systems.  Windows bootloaders see only Windows.  If you install Windows *after* another OS, it'll look like you have only Windows on your system.  So Windows is best installed first.  

Ubuntu bootloader is called grub.  It should see the other OSes, but sometimes on first boot, it sees only its own Ubuntu.  Once you're in Ubuntu, open a terminal (Applications > Accessories > Terminal) and run ```
sudo update-grub
```The next time you boot, the other OSes will be in the list.

It sounds like what may have happened in your case is the bootloader got confused.  Just for the future: that can usually be fixed.  No need to reinstall.

I've never used wubi, so I don't know anything about things specific to it.  In ubuntu generally, the way to find the proprietary drivers you need is to go to System > Administration > Hardware Drivers.  Get a wired connection to the net.  It should scan for the necessary drivers and ask you whether you want to install them.  If there's more than one choice, I think it usually has a recommended option.

If it's confusing, just come back and ask about it. :D

---

### Post by brkearns on 2010-09-28
I have been going through many of the same issues over the past few weeks.  Luckily, I have most of them solved.  The only remaining big obstacle is the PS/2 Synaptics touchpad getting to work correctly.  The first thing you need to do is make sure you uninstall the Dell Data Safe Local Backup in your Windows drives.  That stupid program was writing to a section of the MBR that grub was using and clobbering the grub loader every time you shut down your machine.  That is likely the cause of your boot loader settings disappearing.  Do a fresh install after that and you should be OK in a dual boot setup.

The next thing you need to do is hook up an ethernet cable to your machine and plug it into a wired network that can access the Internet. The reason for this is that the wireless will not work until you do an upgrade.  After a upgrade, things will start to work better.   My Live CD had 2.6.32-21 on it, and things did not really start working right until I upgraded to 2.6.32-24, and upgraded a bunch of other stuff.

---

### Post by quixote on 2010-09-30
Interesting about the "Data Safe" business.  (Ironic name!)

---

### Post by brkearns on 2010-10-01
[LEFT]Yeah -- don't want to slam them too bad because their machines are pretty good for the money.  Google Dell Data Safe and you will see that they should probably have stayed out of that business. Lots of problems, and I ran into one of them with the local backup on a Dell Studio -- would not create recovery media.  

Anyway -- back to the subject here.  Good news is that the touchpad problems seem to be fixed in 10.10.  Running the release candidate now and no problems.
[/LEFT]

---

### Post by saiki4116 on 2010-11-09
i am using 10.10..working properly except that it is not detecting wifi networks properly..

---

### Post by jith87 on 2011-02-20
Hi
I too ve faced a similar problem like this. After installing Ubuntu, once i try to restart the system the boot loader does not list the installed Operating systems. It simply shows the option to  "Repair windows". I ve left with no other choices other than repairing which eventually removes the partiion in which I ve installed Ubuntu. I am not able to log into Ubuntu.

---

### Post by quixote on 2011-02-20
jith87, I'd suggest you start a separate thread because you have a different question.  The problem in your case is probably that grub (the ubuntu bootloader) was installed on a partition rather than the Master Boot Record (MBR) of the whole drive.  Windows sees a problem, but can't boot, and won't step back enough to let ubuntu do the job.  What you need to do in this case is to fix grub, the bootloader.  

When you post your new question, be sure to note which version of ubuntu you're trying to run, and which version of Windows is on your system. The right thing to do varies, depending on that.

The thing to do right now is to get your Windows back to where it boots and doesn't complain.  Once it's repaired itself, then you can reinstall ubuntu.

---

### Post by Mike K on 2011-02-26
For those who have Ubuntu working properly on Inspiron 14R - how about the external monitor? 

 Mike

---

