---
title: "Internet and screen resolution"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Moonbuzz on 2005-10-14
Hello all,

I realise that some, or perhaps ALL of the following is going to put me as the resident newbie, but I've been using 5.04 (Hoary) for several months now, loved every moment, wouldn't touch anything else, and now I've installed Breezy... nothing seems to work the way it used to. 
Just as a side note, I've done a fresh install, not an upgrade. 

I'm not speaking about most of the stuff, just that the screen resolution refuse to go over 1024x768. With Hoary, I added "1280x1024" to the /etc/X11/xorg.conf resolution lines and that did the trick. The trick isn't being done anymore. 

But the more crucial issue. I have no internet, nor do I have any clue how to set it. (I'm using the Windows partition to access the net, which I've hardly used for three months), I have an ethernet card, Aztech ADSL2+ DSL-600E, recognised and operating according to the Network interface. I probably just need to get the DNS stuff, but I don't really know what to do with it. Also, the connection is with a name/password, which I also don't seem to find anywhere to enter... (disclosure: a friend of mine did the Internet stuff on the Hoary... I was too lazy to check it out since :( )
It also adds to a minor issue, when the system boots up, it gets stuck when it tries to update the clock from the net. Anyway to either disable that, or login to the Internet at boot-up?

Again, thanks in advance to everyone.

---

### Post by xyzzyman on 2005-10-14
For your internet, you probably need to configure PPPoE, try this command at a terminal:

```

sudo pppoeconf 

```

---

### Post by mlomker on 2005-10-15
> 
I'm not speaking about most of the stuff, just that the screen resolution refuse to go over 1024x768. With Hoary, I added "1280x1024" to the /etc/X11/xorg.conf resolution lines and that did the trick. The trick isn't being done anymore.


Try **sudo dpkg-reconfigure xserver-xorg** at a prompt.  There are more resolution options in Breezy than there was in Hoary...at least as far as that command goes.
 
> It also adds to a minor issue, when the system boots up, it gets stuck when it tries to update the clock from the net. Anyway to either disable that, or login to the Internet at boot-up?


You can press Ctrl-C.

---

### Post by Moonbuzz on 2005-10-15
Thanks, I'll try it ASAP :)

---

### Post by Moonbuzz on 2005-10-15
Thanks, I now got the Internet part up and running,
However, I still can't get a higher resolution than 1024... I ran sudo dpkg-reconfigure xserver-xorg and chose 1280x1024, but to no avail. Perhaps something specific I need to do there?

---

### Post by mlomker on 2005-10-15
>  Perhaps something specific I need to do there?

What kind of card is it?

---

### Post by Moonbuzz on 2005-10-15
Nvidia GeForce4 MX 440-SE

---

### Post by mlomker on 2005-10-15
[QUOTE=Moonbuzz]Nvidia GeForce4 MX 440-SE[/QUOTE]

I don't have one.  I know a fair bit about ATI.

I think you'll have to [create a modeline]("http://www.sh.nu/nvidia/gtf.php") to add to your xorg.conf file.  It normally isn't necessary for newer monitors--they are supposed to plug-and-play.

You can also look at the /var/log/Xorg.0.log for any clues about why it isn't taking your mode.

---

### Post by zeca_pedra on 2005-10-17
You should open terminal and type
```
sudo apt-get install nvidia-glx nvidia-settings
```

That's the same graphics card I have and never had problems with it
After the prior installation then edit your /etc/X11/xorg.conf by typing
```
sudo gedit /etc/X11/xorg.conf
```

look for Device where it says "nv" and change that to "nvidia". You can also edit the resolutions the way you tried before

Also, all this is in the Ubuntu Unnofficial Guide. I think you should read that because (almost) everything you'll need is covered

Now all should work fine

---

