---
title: "How to repair UBUNTU on dual boot"
date: 2009-05-23
forum: General Help
---

### Post by Dyffo on 2009-05-23
I am running both Windows XP and Ubuntu 9.04 on dual boot.
My problem is that when booting - grub loads - then when I try to install UBUNTU nothing happens - just a blank screen. When I revert to Windows - this installs with no problem.
I really don't want to have to reinstall everything, its not just the data, but loads of programmes are involved.
Any ideas how to fix the UBUNTU ????????

---

### Post by utnubuuser on 2009-05-23
Hi  -- You realy need to be more specific.  When you say "installs", do you actually mean "load", as in 'you've selected the OS in grub, and are trying to load it'?

"Install" means "insert CD and reboot computer.

"Load" or "boot" means " turn on computer after OS is already installed and select which OS to use in grub.

---

### Post by utnubuuser on 2009-05-23
There are tons of threads about "Windows not loading" and Ubuntu not loading" if you'd just google.  Try:> "Ubuntu won't load" or "Windows won't load Ubuntu" or "blank screen ubuntu"

You can also try a different kernel in grub. - When you're in the grub selector window, instead of loading the first entry for Ubuntu, try the next line down.  That is the "recovery" or "single user mode", and see if you can at least get to the command line.

Once you're at the command line, there are several things that can be done to fix a broken system.

---

### Post by whoop on 2009-05-23
> **utnubuuser said:**
> Hi  -- You realy need to be more specific.  When you say "installs", do you actually mean "load", as in 'you've selected the OS in grub, and are trying to load it'?

"Install" means "insert CD and reboot computer.

"Load" or "boot" means " turn on computer after OS is already installed and select which OS to use in grub.
I think he uses the word install for two different operations:
* Installing software
* booting an operating system

He's probably trying to boot ubuntu, and he gets a blank screen (he doesn't get that when booting windows).

I suggest, booting from ubuntu livecd, type in terminal:
```

gksudo gedit /boot/grub/menu.lst

```

and remove " quiet splash" from the kernel line you are trying to boot from. Then restart and boot without livecd choosing for the kernel, which kernel line you modified, in the grub menu.

---

### Post by Dyffo on 2009-05-23
> **whoop said:**
> I think he uses the word install for two different operations:
* Installing software
* booting an operating system

He's probably trying to boot ubuntu, and he gets a blank screen (he doesn't get that when booting windows).

I suggest, booting from ubuntu livecd, type in terminal:
```

gksudo gedit /boot/grub/menu.lst

```

and remove " quiet splash" from the kernel line you are trying to boot from. Then restart and boot without livecd choosing for the kernel, which kernel line you modified, in the grub menu.

Yep you are correct I should have said Boot UBUNTU and yes I get the blank screen which I don't get with Windws.

Will give this a try.

---

### Post by Dyffo on 2009-05-23
> **utnubuuser said:**
> There are tons of threads about "Windows not loading" and Ubuntu not loading" if you'd just google.  Try:

You can also try a different kernel in grub. - When you're in the grub selector window, instead of loading the first entry for Ubuntu, try the next line down.  That is the "recovery" or "single user mode", and see if you can at least get to the command line.

Once you're at the command line, there are several things that can be done to fix a broken system.

Yep I can get to a command line - WHAT DO I DO THEN ?

---

### Post by utnubuuser on 2009-05-23
Though this isn't safe, do:> sudo startx and see if your install is ok.

It isn't safe because you are now in a root environment, and the computer is vulnerable to attack.  I'm suggesting this only to test your installation.  Don't keep it running in that state.

Also, which version of Ubuntu are we talking about?

Because next you'll want to check your Hardware Drivers.  

If you can't get the graphical environment with "startx", you'll need to check your hardware drivers.  In terminal:  > jockey-gtk or > sudo jockey-gtk
If there are drivers listed for your videocard, enable them,
and if there's nothing listed there, in terminal, or at the prompt:>  sudo dpkg-reconfigure xserver-xorgand follow the prompts, then reboot.

---

### Post by Dyffo on 2009-05-24
> **utnubuuser said:**
> Though this isn't safe, do: and see if your install is ok.

It isn't safe because you are now in a root environment, and the computer is vulnerable to attack.  I'm suggesting this only to test your installation.  Don't keep it running in that state.

Also, which version of Ubuntu are we talking about?

Because next you'll want to check your Hardware Drivers.  

If you can't get the graphical environment with "startx", you'll need to check your hardware drivers.  In terminal:   or 
If there are drivers listed for your videocard, enable them,
and if there's nothing listed there, in terminal, or at the prompt:and follow the prompts, then reboot.

Thanks for this - I will give it a go later on today. I am using Ubuntu 9.04 . It seems  that ALL my problems started with a crash when using "Evolution Mail" - I couldn't send or retrieve any emails, I couldn't open Mozilla Web browser, then on a restart I got a blank screen.

---

### Post by Dyffo on 2009-05-24
O.K. Tried everything here - I still cannot get beyond a blank screen.Is it possible to deinstall and reinstall to the same partition. Whatever happens I cannot afford to loose my working Windows application !!!!!!!!!!!!!!!!!!1

---

### Post by Legace on 2009-05-24
> **Dyffo said:**
> O.K. Tried everything here - I still cannot get beyond a blank screen.Is it possible to deinstall and reinstall to the same partition. Whatever happens I cannot afford to loose my working Windows application !!!!!!!!!!!!!!!!!!1

Yes, it's possible.
Insert the Ubuntu Live CD, and then once you're there, open Terminal, type in **gparted** and post a screenshot of it here..

---

### Post by Dyffo on 2009-05-24
This might be stupid, but I have a screenshot, saved, but I just cannot fathom how to paste it or post it as a reply. HELP I am going nuts.

---

### Post by Dyffo on 2009-05-24
> **Dyffo said:**
> This might be stupid, but I have a screenshot, saved, but I just cannot fathom how to paste it or post it as a reply. HELP I am going nuts.

):P HOORAY SUCCESS Screenshot attached  !!!!!!

---

### Post by Dyffo on 2009-05-24
> **Legace said:**
> Yes, it's possible.
Insert the Ubuntu Live CD, and then once you're there, open Terminal, type in **gparted** and post a screenshot of it here..

Screenshot attached !!

---

### Post by lindsay7 on 2009-05-24
Ok, you need to install Ubuntu again. The big problem is you must have had a small amont of space on your drive and Ubuntu install on it. It is only about 2.5 gig. What you need to do is set up a partition for ubuntu. Download Gparted form the internet. It will be a ISO file and burn it to a disk. Delete the ubuntu partitions. and leave it unallocated. Then shrink the windows partition. I suggest that you run defrag in window first just to be safe so that all your data is on the begining of the drive.  The make a partition with all of the unallocated space. Then you can reinstall Ubuntu. Depending on what you want to keep on Ubuntu. Size the partition accordingly. If you are just going to use Ubuntu and not store a lot of stuff on it 10 gigs should be enough for the Ubuntu OS and swap partition.

---

### Post by miegiel on 2009-05-24
Maybe this helps (if it's a GRUB issue):

[_Recovering Ubuntu After Installing Windows_]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by rehilliard on 2009-05-24
I re-installed 9.04 (dual boot with win7) after using win to blow away the partition where  i had 9.04 netbook installed earlier.

funny thing, when doing the install and instructing to use all free space...the bottom graphic showed only 2.5gb to  be used for ubuntu (26gb was free)!! The upper graphic shows the 26gb. I was able to  use the slider to increase the partition size to the 26gb and the install went just fine...so...

Pay close attention to that bottom graphic (if  you choose all free space) and make sure  it matches what you know you have to install into.

Just wanted to pass it along for posterity...

---

### Post by Dyffo on 2009-05-25
> **lindsay7 said:**
> Ok, you need to install Ubuntu again. The big problem is you must have had a small amont of space on your drive and Ubuntu install on it. It is only about 2.5 gig. What you need to do is set up a partition for ubuntu. Download Gparted form the internet. It will be a ISO file and burn it to a disk. Delete the ubuntu partitions. and leave it unallocated. Then shrink the windows partition. I suggest that you run defrag in window first just to be safe so that all your data is on the begining of the drive.  The make a partition with all of the unallocated space. Then you can reinstall Ubuntu. Depending on what you want to keep on Ubuntu. Size the partition accordingly. If you are just going to use Ubuntu and not store a lot of stuff on it 10 gigs should be enough for the Ubuntu OS and swap partition.

O.K. brilliant thanks for that -  can you tell me from the screenshot which is the UBUNTU partition that I should delete ??, and which is the Windows partition to shrink

---

### Post by lindsay7 on 2009-05-25
Ok, using the ISO Gparted disk, delete the partitions inside of sda2 which holds sda5, and sda6. Then delete partition sda2. Leave the space unallocated. Make sure you defage the windows first just to be safe with you data. You can do this from windows. When you are ready, using Grpated, shrink the partitions sda1. Just click on it and use the menu bar. There is a slider on the right hand side of the partition and you just move it to the left. Set the size you want. That should leave more unallocated space. When that is done set the unallocated space up as a new partition, you can format it for the Ubuntu OS at this time if you want Use ext3 or ext4. Now you can install Ubuntu to this new partition.

PS, the Grparted web site has really good support docs on using the program.

---

### Post by Dyffo on 2009-05-25
> **lindsay7 said:**
> Ok, using the ISO Gparted disk, delete the partitions inside of sda2 which holds sda5, and sda6. Then delete partition sda2. Leave the space unallocated. Make sure you defage the windows first just to be safe with you data. You can do this from windows. When you are ready, using Grpated, shrink the partitions sda1. Just click on it and use the menu bar. There is a slider on the right hand side of the partition and you just move it to the left. Set the size you want. That should leave more unallocated space. When that is done set the unallocated space up as a new partition, you can format it for the Ubuntu OS at this time if you want Use ext3 or ext4. Now you can install Ubuntu to this new partition.

PS, the Grparted web site has really good support docs on using the program.

BRILLIANT THANK YOU. All up and running.

---

### Post by lindsay7 on 2009-05-26
Great, glad to help. Enjoy your new system.

---

