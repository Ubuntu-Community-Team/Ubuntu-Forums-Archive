---
title: "I unistalled way too much Gnome"
date: 2008-01-12
forum: Desktop Environments
---

### Post by tmunro55 on 2008-01-12
Hi all,

    I did something really stupid. I uninstalled Gnome, not realising the Xubuntu-desktop requires a lot of it. I've tried all of the following:
apt-get install gnome
apt-get install ubuntu-desktop
apt-get install xubuntu-desktop
aptitude install ubuntu-desktop
aptitude install xubuntu-desktop

In all cases a bunch of stuff is downloaded from the internet, but then I get "Media change:" message and it's looking for "ubuntu 7.10 _Gutsy Gibbon_ Release i386 (20091016.1). I only have the original CD I installed with.

I've also tried boot into the liveCD, mounting the root of my filesystem to /root, and using chroot /root. I still get the Media change: message.

Any help would be greatly appreciated. I don't really want to reinstall.

Thanks.
--
Tim

---

### Post by PeterJS on 2008-01-12
You're on the right track, open synaptic and go to Settings > Repositories and disable the cdrom and enable the internet repositories as needed.

---

### Post by tmunro55 on 2008-01-12
I'm assuming this is with the liveCD approach I tried above. I'll give it a shot.

Thanks.
--
Tim

---

### Post by urukrama on 2008-01-12
> **tmunro55 said:**
> I'm assuming this is with the liveCD approach I tried above. I'll give it a shot.

What (s)he means is that you have the Live/installCD listed as a repository, so that when you want to install something, you need to have the CD in your drive (but not running it as a liveCD).

As mentioned, you can easily disable this in Synaptic. 

You do not need to boot into the LiveCD. Just boot your computer as usual, from the hard disk, then disable the CD in Synaptic, 'Reload' Synaptic (on the menu bar), and install whatever package you want.

You could also do this from the command line, if you want. To do so, you'll have to edit your sources.list file:

> sudo gedit /etc/apt/sources.list

(if you removed gedit as well, use mousepad, or any other simple text editor)

Add a # before the CD line, save, and close the file. Then do:

> sudo aptitude update 

Reinstalling xubuntu-desktop should fix your problem. You can now reinstall it with the following: sudo aptitude install xubuntu-desktop

In case your sources.list file is corrupted, you can generate a new one [here]("http://www.ubuntu-nl.org/source-o-matic/").

---

### Post by tmunro55 on 2008-01-12
My main problem is that I could not "boot as usual" because no GUI would load (that's how much I removed). I only had the text interface. Booting with the liveCD didn't help, because even though I could mount MY system under /root and chroot to my system Synaptic would only update the Live session.

With a bit of poking around I finally figured out how to disable the CDROM in sources.list using vi. So I booted into my text interface, tweaked sources.list and ran apt-get update then apt-get install xubuntu-desktop. Low and behold everything is just fine now.

Thanks to both PeterJS and urukrama for your help with this.

--
Tim

---

