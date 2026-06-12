---
title: "Getting gdm back as default"
date: 2007-12-22
forum: Desktop Environments
---

### Post by jmagick07 on 2007-12-22
I installed kubuntu-desktop, and it asked me to pick a default (kdm or gdm).

I rather don't like the KDE style, and wanna switch back to GDM as the default.  I know I can switch between them in sessions, but how do I make it the default again?


Also, when I installed kubuntu-desktop, it came with all this other "crap" in my Applications list, how can I remove them?  It makes it hard to find the stuff I want now.

---

### Post by barrack on 2007-12-22
At the main log-in screen, in the bottom left hand corner, there is a settings area. There you can "Select Session" and choose GDM. It will ask you if you want to make it default. I had to do this for XGL.

Not sure about the kubuntu applications list.

---

### Post by JoshuaRL on 2007-12-26
I have this problem too.  I really like all three desktops and like the geek parade of showing all my friends what linux can do by switching back and forth to them.  However, when I did

```

sudo apt-get install kubuntu-desktop

```

I decided that I wanted to use kdm as the default desktop manager.  Now I want to switch back because I'm having weird problems launching 3D games with Gnome and kdm.  I tried running

```

sudo apt-get install --reinstall gdm

```

but it fails at that it will change when all sessions of X have stopped running.  I've tried it in Terminal, Failsafe, and Rescue mode.  How do I get gdm back?  Do I just reinstall ubuntu-desktop, or can I reinstall gdm someway?

I do know how to switch desktops from login, but I would like to make gdm the default again.

---

### Post by Tenken on 2007-12-26
[This page]("http://knowledge76.com/index.php/Display_Manager:_Switch_Between_GDM_and_KDM") might be what your looking for.

---

### Post by JoshuaRL on 2007-12-27
That seems to be a more targeted approach to what I'm trying to do and I thank you for it.  However, I still can't get gdm to load as default.  I've run that in rescue mode, which as I understand it doesn't activate X, and it still stalls and says it will apply changes when every session of X is ended.  I can't figure out how to do this.

---

### Post by p_quarles on 2007-12-27
The link that Tenken gave you is the solution to the problem. If you reconfigure GDM (or KDM, for that matter), you will get a dialogue asking you which one you want to use as the default display manager. 

The other way to do it:
```
gksudo gedit /etc/X11/default-display-manager
```
Change:
```
/usr/bin/kdm
```
to
```
/usr/bin/gdm
```

---

### Post by dlegend on 2007-12-27
For removing KDE apps from the gnome menu and vice-versa run the script "menu-cleaner.sh" (provided at the end of this post). If you are worried that it may screw up your menu just make a backup copy of those directories:

> 
    mkdir -p ~/.menu-backup/{gnome,kde}

    cp /usr/share/applications/* ~/.menu-backup/gnome

    cp /usr/share/applications/kde/* ~/.menu-backup/kde


Script: [http://www.programming-designs.com/linux/menu-cleaner.sh](http://www.programming-designs.com/linux/menu-cleaner.sh)

I got this info from [this link](http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/) but their tutorial doesn't work for Gutsy and the menu-cleaner script is no longer available on their site.

Enjoy =)

---

### Post by JoshuaRL on 2007-12-28
Thanks everybody.  And special thanks to p_quarles.

Let me sum up a little as to what I've already tried.

```

sudo apt-get install --reinstall gdm

```

```

sudo dpkg-reconfigure gdm

```

And when I tried both of those from inside an X session, failsafe terminal, or rescue mode the terminal said that it would continue after all the X sessions had closed.  Originally I thought that if I just restarted it would work.  But unfortunately it didn't.  So I'm trying to get gdm as the default desktop manager instead of kdm.

I've had a little experience editing .conf files with xorg.conf because my laptop video card is wonky and needed a fair amount of manual tweaking.  So I feel comfortable with that approach.  So I thank you all for the prompt help and I think I've found my solution.

---

