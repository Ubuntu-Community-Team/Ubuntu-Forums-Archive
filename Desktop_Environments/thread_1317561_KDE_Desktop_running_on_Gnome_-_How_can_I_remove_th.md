---
title: "KDE Desktop running on Gnome - How can I remove the Gnome panel?"
date: 2009-11-06
forum: Desktop Environments
---

### Post by MadnessRed on 2009-11-06
Hi, I am running Ubuntu 9.04. With KDE installed. I am using the gnome session primarily. However, I am useing the KDE Desktop and panels. So kind of a hybrid session. (I like the KDE panel and desktop but I am more comfortable with GNome the rest of the time.)

What I want to do it stop the GNOME-Panel from starting up when I log in. How would I go about doing this?

---

### Post by cptr13 on 2009-11-06
I don't understand this at all...As far as I know...you can't mix the two.  You can use KDE apps inside a Gnome environment and vice versa.  But as far as I know, you can't use the KDE "desktop" while logged into Gnome.

Can you elaborate with specifics?

---

### Post by wojox on 2009-11-06
So log in and use the kde session.

---

### Post by MadnessRed on 2009-11-06
> **cptr13 said:**
> I don't understand this at all...As far as I know...you can't mix the two.  You can use KDE apps inside a Gnome environment and vice versa.  But as far as I know, you can't use the KDE "desktop" while logged into Gnome.

Can you elaborate with specifics?

I am already using the KDE desktop in gnome. What I am trying to do is remove the Gnome panels.

If you have kde and gnome, press alt+f2 and type "plasma"

---

### Post by lovinglinux on 2009-11-06
> **cptr13 said:**
> I don't understand this at all...As far as I know...you can't mix the two.  You can use KDE apps inside a Gnome environment and vice versa.  But as far as I know, you can't use the KDE "desktop" while logged into Gnome.

Can you elaborate with specifics?

Yes, you can.

> **MadnessRed said:**
> I am already using the KDE desktop in gnome. What I am trying to do is remove the Gnome panels.

If you have kde and gnome, press alt+f2 and type "plasma"

See solution [here](http://ubuntuforums.org/showthread.php?t=1291048). Scroll down to step 5. Keep in mind that once you remove the gnome panel, you will lose other functionality, like shortkeys and menus, including alt+F2. So I recommend creating the launchers on step 4, to allow starting gnome-panel if needed. 

I'm currently using KDE, but when I was using that setup, I wasn't able to logout or reboot from plasma.

---

### Post by MadnessRed on 2009-11-07
> **lovinglinux said:**
> Yes, you can.



See solution [here](http://ubuntuforums.org/showthread.php?t=1291048). Scroll down to step 5. Keep in mind that once you remove the gnome panel, you will lose other functionality, like shortkeys and menus, including alt+F2. So I recommend creating the launchers on step 4, to allow starting gnome-panel if needed. 

I'm currently using KDE, but when I was using that setup, I wasn't able to logout or reboot from plasma.

hm, that tutorial is pretty much what i have done already, the bit about gconf I did but it doesn't work. I can't kill gnome-panel. The tut is for karmic though I have jaunty atm.

---

### Post by lovinglinux on 2009-11-07
> **MadnessRed said:**
> ok, many thanks. I have currently managed to mess up my gnome install, playing with netbook-remix so I have kinda gone the otherway, I am running metacity in kde with compiz. Then I applied the Humanity Theme to KDE for consistancy. Looks quite good now. Now I have to decide between nautilus and dolphin.

I also use Humanity theme on KDE. Looks really nice. Additionally, I use the Klearlooks style on KDE applications and QtCurve for Gnome applications.

---

### Post by cptr13 on 2009-11-07
I've heard of this before, but I always assumed people didn't fully grasp the differences between Gnome and KDE.  Are there any screenshots or videos of this?  I'm curious to see it.  The screenshot on your tutorial frankly just looks like KDE with a gnome app and a few gnome icons. Store)

---

### Post by lovinglinux on 2009-11-07
> **cptr13 said:**
> I've heard of this before, but I always assumed people didn't fully grasp the differences between Gnome and KDE.  Are there any screenshots or videos of this?  I'm curious to see it.  The screenshot on your tutorial frankly just looks like KDE with a gnome app and a few gnome icons. Store)

Unfortunately, I'm currently using kde-minimal over a command-line only installation of Ubuntu, so I can't post more screenshots or videos. Essentially, running plasma over Gnome is just like running kde-minimal on Ubuntu, but you don't have to logout and change the desktop environment for the session.

---

### Post by t.rei on 2009-11-07
I understand what you want to do, and the solution depends on some details:

If you want to use krunner on alt+f2 you can just do
```
sudo chmod a-x /usr/bin/gnome-panel
```
effectively removing the permission to e**x**ecute the gnome panel from **a**ll users.
this can be reversed by running
```
sudo chmod a+x /usr/bin/gnome-panel
```

Now, if you want the gnome "Run Application" dialog. That makes it more difficult, as I think it is somewhat linked to having the gnome-panel running.

BUT you can just hide it:
Delete all but one gnome panel, empty it of all apps, make it as small as possible in one corner and set it to auto-hide.
Then run
```
gconf-editor
```
and go to apps -> panel -> toplevels
there should be just one panel below that.
change its settings to: "auto hide size 1" and "animation_speed fast" "hide delay 0" "unhide_delay 3000"

ok, you have a tiny little pixel in the corner now. but put it in the lower right corner, and never worry about it. ;) If you set the panel color apropriately you might be able to set it to just the same color as your kde panel.

Used to run this while back. By now I have one kubuntu system that I use actively and one ubuntu for testing. ;)

---

