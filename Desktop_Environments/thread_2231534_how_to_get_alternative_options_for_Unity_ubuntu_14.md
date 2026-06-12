---
title: "how to get alternative options for Unity ubuntu 14.04"
date: 2014-06-26
forum: Desktop Environments
---

### Post by mandar2 on 2014-06-26
Hello all,

I am sure after posting this many are going to think it has been repeated millions of times.

However, there is no post which demos, how to get an alternative (gnome kde xfce...) with terminal.

i have browsed and found only how to get gnome-session-fallback or installing gnome 3.12.

Further, users discuss problems which i as a beginner then gets confussed.
I am new to Ubuntu and as a os, linux offers this benefit to use more than one de... i think it is a benefit.

Experts: please reply to give a summarized answer to all the posts to switch to an alternative desktop.

thanks,

newbie

PS: my interest any stable good looking alternative DE.

---

### Post by rahul4557 on 2014-06-26
You can check this out..

[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)

---

### Post by Bucky Ball on 2014-06-26
xfce4 as used by Xubuntu:
```

sudo apt-get install xfce4
```

... or search for 'xfce4' and install using Software Centre or Synaptics.

lxde: Same as above but replace xfce4 with lxde in examples.

Once installed, log out, choose the xfce4 or lxde session from the 'Sessions' menu, log in. Done. 

There's a heap of desktop environments to try and they're all about that easy (not KDE). For other DEs, like Mate and/or Cinnamon and a heap of others, just go to their homepages, or search for, say, 'mate ubuntu'.

Just a tip: DO NOT install xubuntu-desktop or any other -desktop. This will drag in EVERYTHING and is like installing Xubuntu or whatever -desktop you are installing right in there with Ubuntu. You will get all the default apps and everything else that comes with that flavour.

The way I've shown you above ONLY installs the desktop environment, NOT everything default from the flavour. Good luck.

---

### Post by grahammechanical on 2014-06-26
You should also be aware that it might be fine to install one alternative desktop environment and you will find some in the Ubuntu software centre but install several alternatives and things do get mixed up. I have tried this just as an experiment and you may find that you need to re-install.

My suggestion would be for you to download the live session image for the Ubuntu flavours and test them out and install one that you like. Just as we dual boot with Ubuntu and Windows so we can dual/triple/quadruple boot with Ubuntu and its flavours.

In Linux a lot of work is done by volunteer developers. And their work is accepted and available for download and installation but we should not think that these alternative desktops are being provided by the official Ubuntu developers and are without flaws and all work together flawlessly. That would be a wrong assumption. 

Edit: A couple of examples of what to expect.

[http://ubuntuforums.org/showthread.php?t=2229765](http://ubuntuforums.org/showthread.php?t=2229765)

[http://ubuntuforums.org/showthread.php?t=2225011](http://ubuntuforums.org/showthread.php?t=2225011)

Regards.

---

### Post by buzzingrobot on 2014-06-26
This page about meta-packages might help: [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages).  

Meta-packages don't actually contain software. But, they trigger the installation of of large collection of packages, like alternative desktop environments. For example, rather than trying to install the hundreds of packages in KDE, simply executing "sudo apt-get install kde-full" would install the entire KDE environment (several hundred packages, about a gig's worth).

Be aware that *removing* a desktop environment after it has been installed is often not nearly as simple. And, as Graham says, mixing and matching on one system can lead to trouble, so the best way to check something out is to boot one of the LiveCD's. 

If you are sure you want to permanently move to another desktop, I'd recommend installing the Ubuntu flavor based on that desktop.

---

### Post by mandar2 on 2014-06-26
Thank you all for contributing!

as per[ grahammechanical]("http://ubuntuforums.org/member.php?u=1087323")      
> My suggestion would be for you to download the live session image for  the Ubuntu flavours and test them out and install one that you like.  Just as we dual boot with Ubuntu and Windows so we can  dual/triple/quadruple boot with Ubuntu and its flavours.


I would say then it is wise to take the advice of pros and stay away from conflicting two or more DEs. It is better use what you have than ending up with an unusable setup.

---

### Post by mandar2 on 2014-06-26
hi guys,

[http://www.htpcbeginner.com/install-gui-on-ubuntu-server-14-04-gnome/](http://www.htpcbeginner.com/install-gui-on-ubuntu-server-14-04-gnome/)

this is what i wanted! just different GUIs

is the link above suitable for noobies?

Please reply, atleast y or n.

---

### Post by buzzingrobot on 2014-06-26
> **mandar2 said:**
> hi guys,

[http://www.htpcbeginner.com/install-gui-on-ubuntu-server-14-04-gnome/](http://www.htpcbeginner.com/install-gui-on-ubuntu-server-14-04-gnome/)

this is what i wanted! just different GUIs

is the link above suitable for noobies?

Please reply, atleast y or n.

Well, it gives very barebones instructions to install various desktop meta-packages on an Ubuntu server installation, which, by default, lacks a GUI.

So, yes, those commands should work, in a narrow sense.  All the caveats mentioned previously in this thread still apply.

---

### Post by mandar2 on 2014-06-26
aahhhh... okay so in short, to go from one GUI to another, may lead to conflicts. Such as missing options or such things.

I also found this: [http://askubuntu.com/questions/147858/how-to-remove-desktop-environments](http://askubuntu.com/questions/147858/how-to-remove-desktop-environments)
and i suppose this also may or may not solve the conflicts coming back to meta stuff.
right?

---

### Post by mandar2 on 2014-06-26
with all the confusion at heart... i decided to jump in. because, I have pretty large amount of space available. n i guess xfce4 isn't that heavy. 

 However, since past few weeks in my ubuntu touchpad on/off toggle isn't working, brightness increase decrease buttons are also behaving odd and aren't at their best as before. i wonder why. I am using lenovo ideapad Z500. Same is the case in unity and newly installed xfce4. 

I already feel like my productivity is increased in xfce4 as the bottom pannel seems to be better in comparison to docks available for unity. Xfce4 isn't that good looking but still it's ok. Internet apps work, multimedia apps work, even code::blocks works with the opencv setup which is in my home folder. Which is obvious i guess. Still i thought i should mention this.

Now i think look into tweaking xfce4 and pimping it up! Any ideas? :D

---

### Post by Bucky Ball on 2014-06-26
Unity and xfce or lxde will reside on the same machine without issue. I have had xfce4, lxde, razor and a couple of others installed on one OS without any apparent issues. If you boot into lxde you're not using Unity or any of the others as well, so ... :-k

If you install a DE and things start getting wobbly, just uninstall it. Simple.

---

### Post by impliedconsent2 on 2014-06-29
Why not just download existing built Ubuntu's with different DEs?  Example:  Want XFCE - [Xubuntu]("http://xubuntu.org") ... Want KDE - [Kubuntu]("http://www.kubuntu.org") ... Want LXDE [Lubuntu]("http://lubuntu.net")...etc... All of these distro's are supported by the Ubuntu community.  My recommendation is to download and load each one on a LIVE USB, play around, and see which one you like best.  Like others have said, multiple DEs on a single Ubuntu install probably is not the best idea.  I do not like Unity either - my favorite Ubuntu flavor this year is Kubuntu.

---

