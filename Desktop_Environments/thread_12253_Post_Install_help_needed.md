---
title: "Post Install help needed"
date: 2005-01-23
forum: Desktop Environments
---

### Post by diskman_1 on 2005-01-23
I just got done installing 4.10 "Warty" on both my P4 and Powermac 4400/200. :)  I have SEVERAL questions.  Please bear with me as I come from a long line of Slackware so  this .deb is new to me..

1- How the heck do I kill the X runlevel?  I dont want X on bootup. The runlevels are not listed in /etc/inittab all that great.   I tried init 2-5 from console but it didn't do anything. 

2- I need the kernel source for my P4 so I can compile my DGE-530t NIC card.  I got the new drivers but I cannot compile without source. :(  Can I just grab the 2.6.8-1 from kernel.org and extract that to /usr/src/linux and it will work?  Or is the source on the install CD somewhere?

3- I would like KDE instead of Gnome.  How do I install that?  :p

4- I would like an IRC program like BitchX or something.  Where can I find a listing of available apt-get programs for IRC for both shell and X?

5- Is there a listing of files that can be downloaded via apt-get somewhere?  I would like some applications but I don't know what to apt-get install..  

6- Any good places for documentation for the advanced user?  Things like the layout, runlevels, package formats, archives etc?

Thanks!

---

### Post by rudiz on 2005-01-23
Here is a guide:

[http://ubuntuguide.org](http://ubuntuguide.org)

an irc-client: is xchat
$sudo apt-get install xchat

---

### Post by shmonkey on 2005-01-23
1. ```
sudo update-rc.d -f gdm remove
``` This will remove the symlinks to gdm from the runlevels. Then reboot or issue the command ```
sudo killall gdm
```

2. Yes but in order to build the kernel you will need to install some dev libraries first. Can't remember what they are off hand (sorry).

3. Well in theory yes, but KDE is not supported, I think you would be  better of using Debian SID if you want KDE.

4. ```
apt-cache search irc
``` can also use use synaptic or aptitude.

5. Synaptic for X and aptitude for the CLI.

6. see last post or [http://www.debian.org/doc/manuals/reference/reference.en.html](http://www.debian.org/doc/manuals/reference/reference.en.html)

---

### Post by diskman_1 on 2005-01-23
Ok, my network interface is not coming up.  How can I configure the interface?  I don't have X or Gnome installed.

I can manually configure it but its getting old everything I reboot. :)

Also, is there a file in the runlevel dir that I can supply boot-time programs into?

Thanks!

---

### Post by diskman_1 on 2005-01-25
Guess not..  Yellowdog 3 it is then.

---

### Post by shmonkey on 2005-01-25
boot up stuff (symlinks) are kept in /etc/rcS.d

To manually configure etho edit /etc/network/interface and /etc/resolv.conf.

---

### Post by farruinn on 2005-01-25
Perhaps you've already installed yellowdog and will never read this, but in the event that's not true...

If you want to use KDE on ppc you'll have to build everything from source.  The Debian APT Howto is excellent: [http://www.nl.debian.org/doc/manuals/apt-howto/index.en.html](http://www.nl.debian.org/doc/manuals/apt-howto/index.en.html)  Look for instructions on building binary packages from debian source packages.

For finding packages use synaptic or 'apt-cache search [package]'  You may have to enable the universe repository to find everything you want: [http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto)

---

