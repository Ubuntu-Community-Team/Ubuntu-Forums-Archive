---
title: "HOW-TO: Beryl Worspaces FIx :)"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by starcraft.man on 2007-04-29
Hi, after quite some work and looking around I have found a fix for Beryl in 7.04. The problem I had was that the workspace options dissapeared when right clicking on a window using the beryl manager.

I searched and didn't see it posted anywhere in this forum so figured I would post it here in my lil guide format, credit goes to this thread though on the Beryl Project forums. (Link [Here)]("http://forum.beryl-project.org/viewtopic.php?f=39&t=6089")

1) Add Beryl Edgy Repos

```
sudo gedit /etc/apt/sources.list
```

Add the following at the bottom:

```
## Beryl Edgy Repo
deb http://ubuntu.beryl-project.org/ edgy main
```

Then of course reload your update manager.

```
sudo aptitude update
```

2) Synaptic Package Manager 

Go to the packet manager System -> Administration -> Synaptic Package Manager

Click on search and enter "libwnck", click ok, then you should see several files returned.

We are interested in:

```
libwnck18
libwnck-common
```

Changes to these files seem to be the trouble. Its easy now to downgrade.

Select libwnck18 and go Package -> Force Version, in the drop down menu select 2.16.1 and push ok. Repeat this for the common package as well. Then push apply and you will downgrade your version of both files.

Reboot your computer and on restart you can now switch workspaces like you used to, perhaps later a patch will be made for beryl to work with 2.18.0 :).

3) If you want to stop the update manager from pestering you to upgrade to 2.18.0 just search for libwnck like before and select each of the two files one at a time and then go System -> Lock Version. 
The only problem with this is you will have to update these two files manually if a new version is released.

PS: I do hope this is formatted properly.

---

### Post by MrGrey1 on 2007-05-07
thank you thank you thank you!!!
Spent 4 hours on this. Genius, pure genius. :)

Edit: Starcraft man I have noticed this seems to only work intermittently. Sometimes I have the right click menu sometimes I don't. Just wondering if you've had the same problem?

---

### Post by alexao on 2007-05-07
anyone know if it's possible to change workspaces with rotating the cube? I would like to change workspace everytime I rotate the cube

---

### Post by ZodiacfreaK on 2007-05-08
hey alexao,
I just had your exact same problem and I finally figured out what I was doing wrong.
Go to Beryl Settings Manager->General Options->
Change Horizontal Virtual Size to 4
Change Vertical Virtual Size to 1
Change Number of Desktops to 1

---

### Post by alexao on 2007-05-08
thanks mate

---

### Post by luvinit on 2007-05-15
Hi this does work, but its worth mentioning that it could cause major trouble for people who don't know what they're doing. Synaptic removed all the main gnome components and emerald from beryl. This means that you can't load up as normal when you reboot. Anyone who is new will no doubt panic at this.  When you are sent to the terminal, as you do when it can't load gnome, you need to type "sudo synaptic". In synaptic reinstall gnome desktop and emerald. You should be ok then.

---

### Post by Kulgan on 2007-05-19
> hey alexao,
I just had your exact same problem and I finally figured out what I was doing wrong.
Go to Beryl Settings Manager->General Options->
Change Horizontal Virtual Size to 4
Change Vertical Virtual Size to 1
Change Number of Desktops to 1

I was having the same problem, and came to this thread by mistake. Good thing I read on. Doesn't it make sense to have the "Number of Desktops" set to 4 if you have four desktops... but no... Thanks!
Now, however, I see why this thread was started in the first place. Lets give it a shot then, shall we...

---

### Post by mustang on 2007-05-26
Thanks for posting this. It works fine here.

---

### Post by Lou Quillio on 2007-06-11
> **ZodiacfreaK said:**
> Go to Beryl Settings Manager->General Options->
Change Horizontal Virtual Size to 4
Thanks for this.  My cube rotation had died after jiggering a new monitor. Though I never touched this Beryl parm, it somehow got set to `1`.  I'd have found it eventually, but was about to give up on it for the night.  Now I can sleep.

LQ

---

### Post by juicymixx on 2007-09-28
> **luvinit said:**
> Hi this does work, but its worth mentioning that it could cause major trouble for people who don't know what they're doing. Synaptic removed all the main gnome components and emerald from beryl. This means that you can't load up as normal when you reboot. Anyone who is new will no doubt panic at this.  When you are sent to the terminal, as you do when it can't load gnome, you need to type "sudo synaptic". In synaptic reinstall gnome desktop and emerald. You should be ok then.

Well, this has happened to me.   I can't "sudo synaptic" since the nvidia drivers aren't right now, and Gtk warns that it can't open the display.

Just wondering what the next step should be..?

---

### Post by Lou Quillio on 2007-09-28
> **juicymixx said:**
> Well, this has happened to me.   I can't "sudo synaptic" since the nvidia drivers aren't right now, and Gtk warns that it can't open the display.

Synaptic's just a GUI front-end to APT, so you can use the [**apt-get**]("https://help.ubuntu.com/community/AptGetHowto") utility from a command line instead.

You'll eventually want to switch to compiz-fusion, though, so a more durable fix would be to do that instead -- but maybe after you get your desktop back.

LQ

---

