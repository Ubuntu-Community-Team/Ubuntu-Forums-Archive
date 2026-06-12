---
title: "I just got dell w/ unbuntu... how can i add XP for dual boot?"
date: 2007-06-22
forum: Dell  Ubuntu Support
---

### Post by mxl360 on 2007-06-22
I just got dell w/ unbuntu... how can i add XP for dual boot?
I'm afraid if I add XP... I will no long be able to choose unbuntu.

---

### Post by steve0921 on 2007-06-22
Adding windows to an ubuntu machine is more difficult than adding ubuntu to a windows machine, because windows assumes it will be the only operating system when you install it.

You can, however, install windows easily to its own partition without harming ubuntu. The trouble comes from the boot loader that decides which operating system to load. The windows one won't cooperate so you'll have to (using an ubuntu live/install cd) fix the ubuntu one: GRUB.

Check out [this information]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") from the ubuntu help site.

---

### Post by mxl360 on 2007-06-22
> **steve0921 said:**
> Adding windows to an ubuntu machine is more difficult than adding ubuntu to a windows machine, because windows assumes it will be the only operating system when you install it.

You can, however, install windows easily to its own partition without harming ubuntu. The trouble comes from the boot loader that decides which operating system to load. The windows one won't cooperate so you'll have to (using an ubuntu live/install cd) fix the ubuntu one: GRUB.

Check out [this information]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") from the ubuntu help site.

Thanks, I will install windows, then add ubuntu.  Do you have a quick link for instructions adding ubuntu dual boot

---

### Post by Crafty Kisses on 2007-06-22
> **mxl360 said:**
> I just got dell w/ unbuntu... how can i add XP for dual boot?
I'm afraid if I add XP... I will no long be able to choose unbuntu.

You don't need XP, you have Ubuntu. ;)

---

### Post by benson444 on 2007-06-22
Well Microsoft's OSs don't play too nice with others. If you install Windows after Linux you'll only have Windows. You're going to need an Ubuntu install CD. One probably came with your new system.

So, setting up a dual-boot from scratch...

The easiest way is to install XP, format the whole drive and when you are given the choice create a new partition of whatever size you want XP to have. Then install Ubuntu.

If you leave an unformatted space on your drive you will have the option to install to largest continuous free space. Choose that and you should have a dual-boot setup.

Or you could Install XP to take up the whole drive and then install Ubuntu. You'll be able to resize the XP partition and install to the rest of your drive.

Install your Linux ditro after Windows.

---

### Post by AdrianVeidt on 2007-06-23
If you alter the default configuration of the operating system, you'll alter the scope of your hardware warranty. No operating system coverage will be offered, and it may be necessary to remove Windows before troubleshooting can be done.

---

### Post by seshomaru samma on 2007-06-23
this is what you do:
create a new partition (with gaparted - if you want more info i can explain)
format the partition as FAT32 
install windows on the new partition

now you will have two OSs , Ubuntu and Windows

the problem is that Windows would overwrite the MBR and so will be able to boot into Windows only
you can solve it by reinstalling Grub (=the Ubuntu bootloader)

the [recovering ubuntu after windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") explains it well, however notice that in step 6 , you will want to go :
```
setup (hd0)
``` and not setup(hd0,3) as it suggests..

---

### Post by Unicast on 2007-06-24
Why not run a virtual instance on XP using Virtualbox? That way there's no need to keep rebooting.

---

### Post by camarojones on 2007-06-24
> **Unicast said:**
> Why not run a virtual instance on XP using Virtualbox? That way there's no need to keep rebooting.

This is probably the better alternative for minor software.

What I did...

Installed XP using whole drive. Updated and got everything set up, antivirus/anti-spyware/etc.

Threw in the Ubuntu disk and rebooted.

During the installation, I chose "Resize and use freed space" (Since I have my WIndows games on it, I am used 50GB for Windows, and left 30 free for linux)

I rebooted and that was it. All done.

Every time you rebbot, you get a choice between Linux and Windows with the default as Linux.

Enjoy!

---

### Post by jppaynesr on 2007-06-24
Unicast - do you have personal experience with Virtual Box? Does it work? Is it hard ot set up? (the manual looks a little complicated) How about VMware, Parallels, etc?

---

### Post by cvclarke on 2007-06-25
Hi, I just got a Dell E520 w/ Ubuntu installed and I want to install XP.  It seems that the easiest way is to wipe the HD, install XP and then reinstall Ubuntu.  The problem is that I have tried to boot to XP and keep getting errors when it tries to boot.  I have deleted all partitions w/ the Ubuntu install CD and still get the same errors.

I would like to completely reformat the HD, but don't seem to be able to get it done w/ the Ubuntu CD, or via other bootable reformatting programs from the web.  Does anyone know how I can just reformat the HD and start again?  It seems like an easy question, but the Dell techies couldn't help and my attempts have only found failure!

Help!

---

### Post by stchman on 2007-06-25
> **mxl360 said:**
> I just got dell w/ unbuntu... how can i add XP for dual boot?
I'm afraid if I add XP... I will no long be able to choose unbuntu.

Since you have Ubuntu why do you need XP unless you are a gamer?

---

### Post by Unicast on 2007-06-25
> **jppaynesr said:**
> Unicast - do you have personal experience with Virtual Box? Does it work? Is it hard ot set up? (the manual looks a little complicated) How about VMware, Parallels, etc?

Yes I've used it, but I've not used it much - it's there mainly for the geek factor! :D

Dead easy to set up.

I pinched the following from this thread: [http://ubuntuforums.org/showthread.php?t=433359&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=433359&highlight=virtualbox)

Step 1: Install and Configure VirtualBox
VirtualBox is one of the best virtualization apps I have ever seen. I put it right up there against VMWare Workstation, and it tends to perform better in my opinion.
In Edgy, you can download and install VirtualBox by either using Automatix ([http://www.getautomatix.com](http://www.getautomatix.com)) or by installing the .deb from [http://www.virtualbox.org](http://www.virtualbox.org)
I personally installed it through Automatix and find that the easiest route as it makes sure you have everything else you need for it. You can find VirtualBox under the Virtualization section of Automatix.

Ok, once you have VirtualBox installed we are going to make a new virtual machine.
Step 1a: Setting Up a Virtual Machine

    * Open up the VirtualBox app by selecting it from Applications->System Tools->InnoTek VirtualBox.
    * Click the “New” button at the top to bring up the New Virtual Machine Wizard.
    * Click Next
    * Type in a name for your Windows installation. I labeled mine: Windows XP Professional, but you can name yours whatever you feel like.
    * Choose your Os Type from the dropdown. (Important note: this seamless setup will only work with a version of Windows that can act as a Terminal Server that means XP Pro NOT Home, and Vista Business or Ultimate, Windows Server 2003, and/or Windows 2000 Professional)
    * Next adjust your base memory size. VirtualBox recommends 192MB for Windows XP, but I personally find that XP runs a bit slow at this level. I have 2GB of RAM on my machine so I gave XP 600 MB. Choose whatever amount you are comfortable with, and this can always be adjusted later.
    * Next we will choose our “hard disk” to boot into. Click the “New” button unless you already have a VirtualBox image ready, then click the “Existing” button.
    * After clicking New, you will be greeted by the Virtual Disk Wizard, click Next
    * Choose whether or not you want a Dynamically expanding image. I personally like using it because I am not entirely sure how much space I will use, but that it is up to you. After choosing, click Next.
    * Pick a name for your image file and adjust the size to the amount of space you would like to offer for your drive. Then click Next.
    * To finish the new drive creation click Finish
    * Your new disk you just created should be selected, click Next.
    * Click Finish to complete setting up your new Virtual Machine


Step 1b: Configuring Your Virtual Machine

    * Select your new machine from the list of machines on the left and click the Settings button at the top of VirtualBox.
    * Select CD/DVD-ROM and click Mount CD/DVD Drive, then choose whether or not you would like to mount your physical CD drive or an iso file. ( I personally ripped my XP Install CD to an ISO file because I think the install goes faster than off the physical CD)
    * Now, select Network and from the “Attached to” dropdown box select NAT
    * Finally, click the OK button to save all of these settings.

Then boot up your VM by opening up Applications->System Tools->InnoTek VirtualBox and then selecting your virtual machine and clicking the “Start” button and the installation starts.

When you're all done I'd recommend installing guest additions which allows you to resize the XP display to match your own display.

This is a great resource too: [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

Any questions ask away!

---

### Post by HermanAB on 2007-06-25
Virtualization is the way to go.  That way you don't need to dual boot, since you can run Windows in a window.

---

### Post by gurdy on 2007-06-26
> **cvclarke said:**
> Hi, I just got a Dell E520 w/ Ubuntu installed and I want to install XP.  It seems that the easiest way is to wipe the HD, install XP and then reinstall Ubuntu.  The problem is that I have tried to boot to XP and keep getting errors when it tries to boot.  I have deleted all partitions w/ the Ubuntu install CD and still get the same errors.

I would like to completely reformat the HD, but don't seem to be able to get it done w/ the Ubuntu CD, or via other bootable reformatting programs from the web.  Does anyone know how I can just reformat the HD and start again?  It seems like an easy question, but the Dell techies couldn't help and my attempts have only found failure!

Help!

I also just got a Dell Dimension E520 w/Ubuntu installed, and I am having the same problem. 

I'm trying to wipe the HD, install XP and then reinstall Ubuntu. When I try to boot XP I get a blue screen with the error message below. How can I reformat the HD and install XP? 

"A problem has been detected and windows has been shut down to prevent damage to your computer. 

"If this is the first time you've seen this stop error screen, restart your computer. If this screen appears again, follow these steps:

"Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHDSK /F to check for har d drive corruption, and then restart your computer.

"Technical information:
*** Stop: 0x0000007B" (etc. --more numbers)

---

### Post by Tethtibis on 2007-06-26
well, honestly, you could put windows on a linux machine, but you'd have to go into window's logical drive and change the boot.ini file to include ubuntu. BUUUT, easiest is always windows then ubuntu. :O)

---

