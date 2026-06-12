---
title: "[SOLVED] Desktop won't fully boot up"
date: 2008-07-21
forum: Desktop Environments
---

### Post by Rustafur on 2008-07-21
Last night I went to uninstall the Evolution email client, and I think I got a bit too carried away with it. I ran a search for "evolution" in the package manager and clicked on "remove" on everything I found that started with evolution and had a green box beside it. Well now my gnome desktop environment won't fully boot up. When Ubuntu boots up, and Gnome desktop starts loading, the only things that fully load are my desktop wallpaper, and whatever icons/files I have on my desktop. I can't even get gedit to start up when I hit Alt+F2. I tried to boot up in safe mode, and repair X, but that didn't work. I've tried every type of rebooting, but I'm afraid that when I went crazy on my evolution uninstall that I may have removed some files that the Gnome desktop needs. That's just a guess, I'm far from a linux veteran. I can still get to the CLI via the Grub boot manager, so if there's some command line "apt-get install *" that would fix my dilemma I can still do that to hopefully save my beloved desktop. Thanks in advance!

---

### Post by wimmelis on 2008-07-21
Hi,


I seem to have run into similar problems, but I only managed to make things worse ... so I am working on a solution to get out of those problems now. 
As far as I get, you might be able to do the following.
Try to before logging in, change your session, to Failsafe gnome, if that works then you can install evolution again and that might solve the problem. 
If that does not work, then try to go to a terminal, using ctrl+alt+F1 for example and try to do the apt-get install evolution or apt-get --reinstall install ubuntu-desktop.
I hope you will be more lucky than me, if not, then we should watch one anothers thread :-)


Wim

---

### Post by smartboyathome on 2008-07-21
You just uninstalled gnome-panel, you will only have to reinstall that to get it back. Hope this helps. :)

---

### Post by Rustafur on 2008-07-21
I think it will, thanks! 

I tried to run apt-get install gnome-panel at the root command line and I saw some of the files I removed from earlier. The only problem is that I can't download them since I don't have a network connection when I boot into root command line. So could someone please show me how to either a) connect to my network in the root command line, or b) show me how to re-direct my package manager in the root command line to point to the Ubuntu Install CD? Or heck, if you're feeling adventurous show us how to do both! ;) Thanks again!

---

### Post by smartboyathome on 2008-07-21
When you boot up, use control+alt+f1, log in, and install it from there, and then control+alt+f7 to get back to gdm and log in.

---

### Post by lswb on 2008-07-21
Network:
If your internet connection is through wired ethernet connected to a router or DSL or cable modem, try this after you get to a cli

(In recovery mode you don't need sudo)

ifconfig eth0 up
dhclient eth0

To add cd to available repositories for apt-get: 
cd /etc/apt
Make a backup of the file soureces.list just in case
cp sources.list sources.list.backup

If you have a text editor you know how to use, open sources.list and add this line:
```

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

```

I think the nano editor is included in a default installation, so you would use the command "nano sources.list" or you could use vi or whatever your comfortable with. 

If there is no editor you can enter at the cli
```

echo "deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted" >>sources.list

```
Make sure that you use 2 (>>) of the '>' in the line, this will add the line to the end of the file.

---

### Post by Zip247 on 2008-07-21
I had the same problem, I removed evolution and the panels would not load.

I started by following Smartboyathome's advice of logging into ubuntu, switching to terminal with ctl+alt+F1,  then sudo apt-get install gnome-panel.  This will let your panels come up...I still had errors with some of the applets in the panels.  I went to synaptic and installed gnome-applets and now all is well.

Hope you can get yours working again.

---

### Post by Rustafur on 2008-07-22
Thanks smartboyathome and lswb for your help! I was able to install gnome-panel by getting to the cli via Ctrl+Alt+F1. And after a reboot my gnome panel came back, sweet! I did have to reinstall gnome-applet like wdecker did, so thanks for the heads up on that wdecker. My only other hitch was that I had to readjust some of my X settings (reselect my monitor, adjust my resolution) and get compiz and my gnome theme all had to be redone as well. Everyone gets a thanks from me!

Another prime reason why this forum is without a doubt the most helpful and greatest bunch of computer geeks on the net!

---

