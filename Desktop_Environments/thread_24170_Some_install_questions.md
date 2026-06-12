---
title: "Some install questions"
date: 2005-04-05
forum: Desktop Environments
---

### Post by SquireSCA on 2005-04-05
I installed ubuntu 5.04 and had some issues, forcing me to go back to Suse for the time being untill I can figure out how to make this all work.

My install issues, are that I have seen several different ways to do things, some of them seem easier, some are downright crazy...

The things that I need to get me off the ground are :

1) Easy noob-proof way to install the *latest* NVidia drivers for a 6800GT
2) Gnome does not automount my 250gb SATA storage drive(ext3), I need it to do that.
3) Easily set up extra repositories for Synaptic.

---

### Post by Nis on 2005-04-05
1) I posted this in the other thread: update using Synaptic and install nvidia-glx, which is at version 1.7174.  Run the below in a terminal:
```

sudo nvidia-glx-config enable

```
Now edit /etc/X11/xorg.conf and delete the line that reads 'Load "dri"'.
If you want to get rid of the Nvidia splash screen add the following right under 'Driver "nvidia"':
```

Option "NoLogo" "True"

```
If you want a little more speed add this experimental option right under 'Driver "nvidia"'
```

Option "RenderAccel" "True"

```
Now restart X (ctrl+alt+backspace) or reboot.

---

### Post by Nis on 2005-04-05
2) Not sure how but we'll get it working together. :)

3) Try using the [Hoary After-Install Helper](http://www.ubuntuforums.org/showthread.php?t=22860) (shameless self promotion  :oops: ).  It will let you easily install Flash, Java, the w32codes, libdvdcss, and setup Totem to play embedded web media (like at [www.apple.com/trailers/)](www.apple.com/trailers/)).  It adds the Ubuntu backports hoary-extras repository to /etc/apt/sources.list; hopefully this repository (and the rest of Ubuntu backports) will contain everything you'll need eventually.

---

### Post by SquireSCA on 2005-04-05
I installed the NVidia drivers through Synaptic.  I deleted the load DRI entry from the config file.

I used apt-get to install and enable the nvidia-settings stuff.

No dice.

glxgears no longer even runs, and when I run the nvidia-settings, the tabs are empty...

Also, I did get many of my apps installed, like dvd playback, XMMS, Mplayer, Xine, and it went well, except that my DVD drives don't have DMA enabled, so DVD playback is choppy.

Drives are a 16x Liteon DVDROM and a Samsung 16x Dual-Layer DVDRW

---

### Post by Buffalo Soldier on 2005-04-05
Was there any error in running **sudo nvidia-glx-config enable**?

---

### Post by SquireSCA on 2005-04-05
[QUOTE=Buffalo Soldier]Was there any error in running **sudo nvidia-glx-config enable**?[/QUOTE]
 None.  I ran it and it gave no errors, just went back to the prompt.

---

### Post by Nis on 2005-04-05
Nvidia issues first:
Can you post the output of cat /etc/X11/xorg.conf and /var/log/Xorg.0.log?  After you installed the nvidia drivers and edited /etc/X11/xorg.conf did you restart X?  After you answer these then we can narrow down the problem.

The DMA issue:
The file /etc/hdparm.conf controls setting DMA and such at boot.  Here's the important part of mine:
```

/dev/hda {
        mult_sect_io = 16
        dma = on
}

/dev/hdb {
        dma = on
}

/dev/hdc {
        mult_sect_io = 16
        dma = on
}

/dev/hdd {
        dma = on
}

```
hda and hdc are hard discs and hdb and hdd are a DVD-ROM drive and CD-RW drive, respectively.  Try adding similar lines to /etc/hdparm.conf (replacing drive letters where necessary) and then running:
```

sudo /etc/init.d/hdparm restart

```
If that returns successfully post the output of the follow:
```

for disc in `ls /dev/hd?`; do sudo hdparm $disc; done

```
The ` in the code are backticks (right next to 1 on the keyboard and also the ~ key).  These are very important in the code above and CANNOT be replaced with quotes.

If you see results specifying 'dma = on' then you can do the following to ensure DMA is turned on for the right drives at boot
```

sudo mv /etc/rcS.d/S07hdparm /etc/rcS.d/S41hdparm

```

Let me know what happens.

---

### Post by SquireSCA on 2005-04-05
You know what?  Listen, I appreciate the help, I really do.  I am just not ready for this.

I have wasted 7 hours today trying to get an OS to do the basic things that it should do out of the box.  This is not an OS for Linux newbies, not by any stretch.  

Things should not take this much work.  

I am headed back to either Suse or Windows.  I cannot spend thins much time trying to make my PC do the basic things it is designed to do. 

WHen I have to put this much time and effort into something that should take a couple mouse clicks in another OS, it simply isn't worth it anymore...  Any benefit that the OS might offer went right out the Window.  I don't care if it's free.  It is worth $100 to me to have something that just does what it is supposed to.

Again, thanks for the effort, I am sorry, but I don't want to waste anyone else's time pursuing this foolishness.

---

### Post by Nis on 2005-04-05
[QUOTE=SquireSCA]You know what?  Listen, I appreciate the help, I really do.  I am just not ready for this.

I have wasted 7 hours today trying to get an OS to do the basic things that it should do out of the box.  This is not an OS for Linux newbies, not by any stretch.  

Things should not take this much work.  

I am headed back to either Suse or Windows.  I cannot spend thins much time trying to make my PC do the basic things it is designed to do. 

WHen I have to put this much time and effort into something that should take a couple mouse clicks in another OS, it simply isn't worth it anymore...  Any benefit that the OS might offer went right out the Window.  I don't care if it's free.  It is worth $100 to me to have something that just does what it is supposed to.

Again, thanks for the effort, I am sorry, but I don't want to waste anyone else's time pursuing this foolishness.[/QUOTE]
 SquireSCA please check your private messages.

---

