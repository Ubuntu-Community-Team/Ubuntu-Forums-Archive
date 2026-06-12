---
title: "All methods of disabling the touchpad while typing are out-of-date"
date: 2013-02-03
forum: Desktop Environments
---

### Post by LazarusW on 2013-02-03
I'm trying to disable the touchpad while typing. This is a long-standing problem, and there are answers [here]("http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html"), [here]("http://ubuntuforums.org/showthread.php?t=271052&highlight=syndaemon"), [here]("http://www.ashokgelal.com/2008/04/disable-accidental-touchpad-tapping-while-typing/"), and [here]("http://forums.bodhilinux.com/index.php?/topic/2033-disabling-touchpad-while-typing/"). There's even an official, Lubuntu-specific answer [here]("https://help.ubuntu.com/community/Lubuntu/Mouse"). Unfortunately, it refers to the editing of a file that either does not exist or cannot be found with catfish. Perhaps part of the problem is that I've never been able to find the elusive ~/.config/ folder. 

I was derailed by the touchpad more than a dozen times while composing this post, so perhaps I should turn off the computer and, while waiting for help, pass the time embroidering a big scarlet "N" for "n00b" to wear on my chest. Speaking of help, any would be appreciated.

---

### Post by deadflowr on 2013-02-03
Don't no much about touchpads and the such.

But you should be able to find the ~/.config folder by clicking on the menu item view and the show hidden folder and/or files.

the ~ is a shortcut symbol for your home folder. (It's easier to type ~/foldername/file than /home/mylongusername/foldername/file)  so this is hidden in that area.

---

### Post by VeeDubb on 2013-02-03
Deadflower is absolutely correct, but just in case any neophite gets confused by it (I certainly found it confusing early on) let met explicitly clarify one point.

```
~/
``` means the exact same thing as ```
/home/username/
```

---

### Post by sudodus on 2013-02-03
> **LazarusW said:**
> I'm trying to disable the touchpad while typing. This is a long-standing problem, and there are answers [here]("http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html"), [here]("http://ubuntuforums.org/showthread.php?t=271052&highlight=syndaemon"), [here]("http://www.ashokgelal.com/2008/04/disable-accidental-touchpad-tapping-while-typing/"), and [here]("http://forums.bodhilinux.com/index.php?/topic/2033-disabling-touchpad-while-typing/"). There's even an official, Lubuntu-specific answer [here]("https://help.ubuntu.com/community/Lubuntu/Mouse"). Unfortunately, it refers to the editing of a file that either does not exist or cannot be found with catfish. Perhaps part of the problem is that I've never been able to find the elusive ~/.config/ folder. 

I was derailed by the touchpad more than a dozen times while composing this post, so perhaps I should turn off the computer and, while waiting for help, pass the time embroidering a big scarlet "N" for "n00b" to wear on my chest. Speaking of help, any would be appreciated.

Try installing ***Touchpad-Indicator*** according to this link

[[COLOR="Red"]https://help.ubuntu.com/community/SynapticsTouchpad[/COLOR]]("https://help.ubuntu.com/community/SynapticsTouchpad")

I use it with Lubuntu in an old IBM Thinkpad.

---

### Post by bogdarnet on 2013-02-03
Have you tried (at a command line)

 xinput list       
 
 xinput float # 

where # is the ID # of the touchpad?

(P.S. Used this method in Gnomish Ubuntu... not sure if it'll work with LXDE or not...)

---

### Post by bogdarnet on 2013-02-04
Checked out Lubuntu in virtualbox, seems like this should work.

> **bogdarnet said:**
> Have you tried (at a command line)

 xinput list       
 
 xinput float # 

where # is the ID # of the touchpad?

(P.S. Used this method in Gnomish Ubuntu... not sure if it'll work with LXDE or not...)

---

### Post by diana.artemis on 2013-07-18
> **LazarusW said:**
> I'm trying to disable the touchpad while typing... There's even an official, Lubuntu-specific answer... Unfortunately, it refers to the editing of a file that either does not exist or cannot be found with catfish. Perhaps part of the problem is that I've never been able to find the elusive ~/.config/ folder

The file is no longer in that location. Here's what you now need to do:

Go to LXTERMINAL and type:

sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

Add the following as the last line in the file:

syndaemon -d

Save and reboot. 


You should now find that Touchpad is disabled for 2sec after typing

HTH

---

