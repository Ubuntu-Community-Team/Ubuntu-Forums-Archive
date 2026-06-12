---
title: "Need Help on Ubuntu boot problems"
date: 2009-04-23
forum: General Help
---

### Post by cookiedemkp on 2009-04-23
Linux OS - Ubuntu 8.10

I seem to have a problem here. One day, i was able to get on the internet so i started to download updates for ubuntu, when i decided that i would update-initramfs so i did and used the option -u. So it did some stuff and finally when it was done, i rebooted linux and tried to boot it back up. The boot splash screen loads fine, but then it drops me to a command line and asks me to log in. If i do, i can use basic terminal commands, and grub, but ubuntu will never boot it just goes back to a command line. Then I used grub and used find /boot/grub/menu.lst and it couldn't find the file, so i used some cd's and ls's and got to my /boot folder, when i found that /grub was no longer in there, so basically grub is gone i cant figure out how to get it back. Is there anyway i can reinstall grub without reinstalling ubuntu, so it will work again? Any help is appreciated.

---

### Post by HankB on 2009-04-24
You shopuld be able to restore grub without a full reinstall. One thing you'll find helpful is a live CD. One that might be particularly helpful is the Super Grub CD.

You might also find some useful information here:
[http://ubuntuforums.org/showthread.php?p=5895332#post5895332](http://ubuntuforums.org/showthread.php?p=5895332#post5895332)

Good luck!

-hank

---

### Post by cookiedemkp on 2009-04-24
I looked at the article, but didnt find anything particularly useful. But i have been trying to run grub-install to reinstall it and I either get Invalid device requested, or when i figure out the device ubuntu is on, it tells me that it count mount the partition because it's read-only. I basically know how I can go about reinstalling grub, but either I cant come up with a valid device string, or it just wont let me do it.

---

### Post by HankB on 2009-04-24
Sorry I could not have been more help. Having recently replaced the drive in my laptop and having run afoul of grub, I feel your pain. Unfortunately my stumbling into a solution leaves me pretty far from being knowledgeable.

Do you know why the device is mounted read only? Sometimes that happens when mount determines that the drive was not properly unmounted. That is its way of telling you that you need to fsck the drive before you can mount it normally. You should be able to fsck with it mounted read only and then remount it read/write once it is clean.

If I were, I would pursue the the read-only mount question. It may not be the right answer, but it's the best thing I can think of offhand. Is it possible that you still do not have the correct device?

-hank

---

### Post by jamessnell on 2009-04-24
For what it's worth, some times I troubleshoot boot issues using the Super Grub Disk. You can go download & burn an ISO from their website, I've found to be quite helpful in navigating some of the more obscure configurations required to get grub to boot bizarre configurations. 

Sounds like you don't need nor want to use that here, but it's a good tool to keep in mind when you get stuck.

---

### Post by cookiedemkp on 2009-04-25
Well after all, I decided to reinstall ubuntu completely, so i did a backup on everything in ubuntu with tar, and put the .tgz file in windows. So i have two last questions. Number 1, i used the tar command to unzip the file back into ubuntu to replace my folders and programs, and when i rebooted, i got the original issue of the login screen, so would this mean that my boot folder that got backed up is causing the problem, and if so, how can i restore my files from the backup without restoring the boot folder?

Second question: after reinstalling ubuntu with the LiveCD, it seems that grubs boot loader has taken over in place of windows' bootloader, how can i get back to using windows' bootloader, as i prefer to use that one instead? Will the super grub disk help me with this?

---

### Post by DigiConstructor on 2009-04-25
Re: the second questoin, this may help...
Do you mean you want Windows to load by default?  
You can use "apt-get install startupmanager" to give you a gui to set Windows to load by default and time it out to a few seconds if you don't want to wait long.  I had to install it, remove it and reinstall it for it to unpackage with no errors for some reason, but it gave me a nice gui to set my default OS and timing.  It put it under System-Administration.
Once Windows loads up you should be able still use the Windows boot.ini or Windows start settings like you normally would.  **[This post]("http://ubuntuforums.org/showthread.php?t=844559")** includes other grub config options 

Re: the first question, I would hesitate overwriting your programs and use apt-get install or the package manager to reload the programs you want, and selectively copy over config files if needed, but I am somewhat novice and wouldn't want to have to figure out how to make the programs work with the new setup.  You should be able to untar your whole backup into a safe subfolder of your home folder, and copy and paste over only what you need, rather than overwriting everything.  I would rather let the new system re-install things how it wants so it sets up any links or whatever as needed.  I think there should be no problem restoring files to your user home directory though.

---

### Post by cookiedemkp on 2009-04-25
Thanks for the tips. I'll do what i can to get back what I want but more than likely ill have to redownload everything, but what i meant by the windows bootloader is that when windows is installed it has its own bootloader where it shows Microsoft Windows Vista and also Ubuntu when its installed and you can use the arrows keys to select one, its very similar to grub bootloader but i prefer windows', so i need to figure out how to get it back. Thanks for the help everyone!

---

