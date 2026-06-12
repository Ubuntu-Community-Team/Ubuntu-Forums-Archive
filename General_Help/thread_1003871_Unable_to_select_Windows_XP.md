---
title: "Unable to select Windows XP"
date: 2008-12-06
forum: General Help
---

### Post by igneousquill on 2008-12-06
I just completed installation of Ununtu for dual boot.  Unfortunately, every time I try to restart the computer and select Windows instead of Ubuntu, the up and down arrows don't work.  What am I doing wrong?  My wife and kids need Windows and we don't want to lose access to our files over there.

Again, on boot up I have a dark screen for ten seconds that tells me to use the up and down arrows to select the OS, but nothing moves when I try and it proceeds to boot up in Ubuntu?

BTW, is there any way to make it default to Windows?

Any help would be appreciated.

---

### Post by castlefox on 2008-12-06
Did you install Ubuntu with Wubi in windows XP.  

On my computer if I dont press anything the computer will automatically boot up in Windows xp unless you selecting ubuntu in the 10seconds it gives you.

---

### Post by eBoxNet on 2008-12-06
Do you use a usb keyboard?
if you do you have to enable legacy usb support from your bios in order to make it work.

edit : you can edit this file /boot/grub/menu.lst in order to make windows default on your boot loader.

---

### Post by igneousquill on 2008-12-06
> **eBoxNet said:**
> Do you use a usb keyboard?
if you do you have to enable legacy usb support from your bios in order to make it work.

edit : you can edit this file /boot/grub/menu.lst in order to make windows default on your boot loader.

where do I edit the file?

---

### Post by igneousquill on 2008-12-06
> **castlefox said:**
> Did you install Ubuntu with Wubi in windows XP.  

On my computer if I dont press anything the computer will automatically boot up in Windows xp unless you selecting ubuntu in the 10seconds it gives you.

I installed Ubuntu 8.10 with its own partition so I'd be able to choose between Windows XP and Ubuntu.

---

### Post by eBoxNet on 2008-12-06
try this on a terminal windows : sudo gedit /boot/grub/menu.lst

---

### Post by HermanAB on 2008-12-06
Just change the 'default' number in menu.lst to what you want.  Start counting at zero, so Windows will probably be the third entry and therefore 2.

---

### Post by igneousquill on 2008-12-06
> **eBoxNet said:**
> try this on a terminal windows : sudo gedit /boot/grub/menu.lst

thanks.  I did that, then it asked me for my password.  Numbers lock is on but nothing appears when I type.

---

### Post by eBoxNet on 2008-12-06
when you type the password the line is blank
just type in your pass and hit enter.
don't expect to see *****

---

### Post by TeXtonyx on 2008-12-06
> **igneousquill said:**
> I just completed installation of Ununtu for dual boot.  Unfortunately, every time I try to restart the computer and select Windows instead of Ubuntu, the up and down arrows don't work.  What am I doing wrong?  My wife and kids need Windows and we don't want to lose access to our files over there.

Again, on boot up I have a dark screen for ten seconds that tells me to use the up and down arrows to select the OS, but nothing moves when I try and it proceeds to boot up in Ubuntu?

BTW, is there any way to make it default to Windows?

Any help would be appreciated.

Ubuntu's grub is installed in the MBR. If you have the XP install
cd you can use Recovery Console (the first Repair option) and
execute fixmbr, fixboot, and bootcfg /rebuild at the Command Prompt.

Then you need to download free Bootpart which you can use to add
Ubuntu to the boot.ini boot menu. That's a little work and some
people don't have an XP install cd but a manufacturer Recovery
cd which doesn't work. So its up to you.

How come the mouse worked when you installed Ubuntu and used it
a bit if it needed a legacy driver? And wasn't the mouse working
before you installed Ubuntu when using XP?

---

### Post by igneousquill on 2008-12-06
> **eBoxNet said:**
> when you type the password the line is blank
just type in your pass and hit enter.
don't expect to see *****

got it.  thanks!  now what?

---

### Post by MarblePanther on 2008-12-06
There is an easier solution if you want to edit grub with a gui.

Just go into your synaptic package manager and search for "startup-manager" and install it.

Very nice little program.  Easier than editing conf files.

---

### Post by eBoxNet on 2008-12-06
Follow this :
> **HermanAB said:**
> Just change the 'default' number in menu.lst to what you want.  Start counting at zero, so Windows will probably be the third entry and therefore 2.

---

### Post by Slim Odds on 2008-12-06
> **TeXtonyx said:**
> Ubuntu's grub is installed in the MBR.

FYI, that is the default, but it can be changed.....

---

### Post by igneousquill on 2008-12-07
> **MarblePanther said:**
> There is an easier solution if you want to edit grub with a gui.

Just go into your synaptic package manager and search for "startup-manager" and install it.

Very nice little program.  Easier than editing conf files.

I did this, it said the installation was successful, and for good measure I rebooted.  No improvement,though.  It takes me to the screen to choose the OS to boot, gives me 10 seconds to choose but won't respond to my keystrokes.

Thanks for the suggestion,though.

---

### Post by igneousquill on 2008-12-07
> **eBoxNet said:**
> Do you use a usb keyboard?
if you do you have to enable legacy usb support from your bios in order to make it work.

edit : you can edit this file /boot/grub/menu.lst in order to make windows default on your boot loader.

It's too late now, but this is the problem.  I modified menu.lst to have windows boot up, but it failed because (though I counted correctly, including 0) it has the wrong header highlighted and fails.  It tells me to hit any key to continue, but since (as I now understand) the system isn't recognizing the usb keyboard during boot up, it just sits there.

I tried booting with the live CD.  That's how I'm writing this message.  Unfortunately, with the live CD I am unable to change the menu.lst back to default to ubuntu or over to windows.

What now?  I assume I'm going to have reinstall Windows, then Ubuntu later if I can ever fix the usb keyboard problem.  Does all this sound correct?

---

### Post by MarblePanther on 2008-12-07
I would assume it is your BIOS that is giving you your trouble with not recognizing it, not Ubuntu.

I would say either get a new keyboard that is compatible with your BIOS or try researching this problem on you computer-maker's site forums.  Maybe someone has figured out the issue there.

---

### Post by igneousquill on 2008-12-10
> **MarblePanther said:**
> I would assume it is your BIOS that is giving you your trouble with not recognizing it, not Ubuntu.

I would say either get a new keyboard that is compatible with your BIOS or try researching this problem on you computer-maker's site forums.  Maybe someone has figured out the issue there.

Yep, it was in BIOS.  the USB keyboard wasn't being recognized.  Since there's no PS/2 connection port on my computer and it was 2am by the time I identified the problem, I did a full installation.  My important info was backed up to three CDs anyway.  So far my family is happy with Ubuntu, and I love it.  

My thanks to everyone on this forum who stepped up with advice.  It was much appreciated.

---

