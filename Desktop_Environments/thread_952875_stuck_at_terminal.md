---
title: "stuck at terminal"
date: 2008-10-19
forum: Desktop Environments
---

### Post by Erewhonman on 2008-10-19
While attempting to replace Alsa i lost GUI interface.  When I boot up my Acer laptop in Ubuntu all I get is a command line.  Tried all the Alt + Function combinations and various other ideas but no go!  What line commands will get me out of the terminal and back in the windows-like environment? Thanks in advance.

---

### Post by anystupidname on 2008-10-19
/etc/init.d/gdm restart?

What specifically was done while "attempting to replace ALSA"?

---

### Post by redbrain on 2008-10-19
You could try:

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/]("http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/")

Which just means if you are loged in as root do :
dpkg-reconfigure xserver-xorg

or: sudo dpkg-reconfigure xserver-xorg
This will reconfigure X to what it was before. Its pretty useful if everything gets messed up ;)

I know i had to do it a while to setup my dual screen properly until i realised the nvidia settings manager did it automaticaly for me haha

---

### Post by lswb on 2008-10-19
If you are running hardy you can 1st try starting in recovery mode and selecting the "repair X" menu choice. If that doesnt work, try the command that anystupidname suggested but using sudo, i.e:

sudo /etc/init.d/gdm restart

If the gui desktop doesn't start up with that command, then try typing
startx
(sudo is not used with the "startx" command)

In either case post your results here: whether the desktop starts or if not, what errors are reported, and include what version of ubuntu you are using, (ubuntu 8.04, kubuntu 7.10, etc.)

---

### Post by Erewhonman on 2008-10-20
Running Hardy.  Trying to set up Skype sound I lost connection with the sound card on my Acer Aspire 2920. In trying to restore it I changed something on Alsa from a suggestion I read in Ubuntu forum.  I then lost complete connection with GUI.  

I tried all of the suggestions just received but nada.  Thanks for the suggestions.  I may have to reload Ubuntu if there are no other suggestions.  I do not know exactly what I did because my bookmarks are on the inaccessible ubuntu.  I dual boot and so I am on windows now.  Thanks for any suggestions.

---

### Post by lswb on 2008-10-20
We can help more effectively if you provide this information:
What desktop do you run? Gnome/ubuntu, KDE/kubuntu, XFCE/xubuntu ?
Do you get a text-mode menu when it starts, with choices of "Repair broken packages, Drop to root shell, Try to fix X server, resume normal boot" ?
Do you get a login prompt when the system starts?
If no menu or login prompt, what is the prompt on the command line you get? Do you see anything about "busybox" or initram?

---

### Post by Erewhonman on 2008-10-20
> **lswb said:**
> We can help more effectively if you provide this information:
What desktop do you run? Gnome/ubuntu, KDE/kubuntu, XFCE/xubuntu ?
Do you get a text-mode menu when it starts, with choices of "Repair broken packages, Drop to root shell, Try to fix X server, resume normal boot" ?
Do you get a login prompt when the system starts?
If no menu or login prompt, what is the prompt on the command line you get? Do you see anything about "busybox" or initram?

I run Gnome/ubuntu and I get the text-mode messages at start-up with all the choices, all of which I have tried, unsuccessfully.  I get is the login prompt and successfully can login.  Thereafter I have no success in getting back into the Gnome interface. I have seen nothing of "busybox" or initram.  Thanks again.

---

### Post by lswb on 2008-10-20
OK, go ahead and log in. Either using the recovery mode root prompt or using sudo as a regular user, issue these commands:

sudo apt-get install ubuntu-desktop gdm

If there are any errors make note of them & post here.

Restart afterwards. If necessary use the recovery menu and select the "repair X server" choice again. Let us know what happened.

---

### Post by Erewhonman on 2008-10-20
> **lswb said:**
> OK, go ahead and log in. Either using the recovery mode root prompt or using sudo as a regular user, issue these commands:

sudo apt-get install ubuntu-desktop gdm

If there are any errors make note of them & post here.

Restart afterwards. If necessary use the recovery menu and select the "repair X server" choice again. Let us know what happened.


OK, entered 
sudo apt-get install ubuntu-desktop gdm

Got a list of errors or failures starting with the advice that 35 of the files were not loaded, only three were.  I wrote down some of the later errors as follows:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.102_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.102_i386.deb).  Could not resolve ca.archive ubuntu.com

E: Unable to fetch some archives, try running apt-get update or apt-get --fixmissing

But there was a full screen of similar notice relative to the other files that could not be recovered.

---

### Post by benerivo on 2008-10-20
You have some bad sounding errors, and i would reinstall. You can recover bookmarks, etc by loading the ubuntu live cd, mounting the problematic ubuntu partition and copying what you need. For example the bookmarks should be in /home/bobby/.mozilla/65sdf4.default/. In fact you could just copy the ~/.mozilla folder and when you reinstall just paste it in to your new home directory before you ever use firefox.

I'm sure your current problems are fixable. Did you try try running apt-get update or apt-get --fixmissing?

---

### Post by lswb on 2008-10-20
> **Erewhonman said:**
> OK, entered 
sudo apt-get install ubuntu-desktop gdm

<...snipped...>

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.102_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.102_i386.deb).  Could not resolve ca.archive ubuntu.com

E: Unable to fetch some archives, try running apt-get update or apt-get --fixmissing

But there was a full screen of similar notice relative to the other files that could not be recovered.

It appears you don't have internet access either. I sure hope that Intrepid is configured so the network comes up without the GUI, that's a real oversight in Hardy. 

If you have a live CD you can try this command:

apt-cdrom add

If you have a proper entry for mounting a CD in your /etc/fstab (Pretty sure it's in the default /etc/fstab file, so you should be OK there) it will prompt you to insert the CD. Follow the prompts and then try   
apt-get install ubuntu-desktop
again.

If you want to try manually connecting to the internet, it's typically fairly easy for wired ethernet. Wireless is somewhat more complicated depending on security settings. You can search the forum for methods and to get an idea of the information we will need to know if you need more help.

---

