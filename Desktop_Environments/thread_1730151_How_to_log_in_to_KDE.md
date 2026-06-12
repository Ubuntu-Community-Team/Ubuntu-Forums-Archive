---
title: "How to log in to KDE?"
date: 2011-04-15
forum: Desktop Environments
---

### Post by Mercury048 on 2011-04-15
I installed Ubuntu 10.10 a few weeks ago. I want to try KDE, so I went to Synaptic and installed kubuntu-desktop.

Now my startup and shutdown screens both say kubuntu (!) - BUT I still get logged into Gnome automatically. If I log out, there are no options (that I can see) on the login screen that allow me to choose a different desktop.

What am I missing?! :confused: And how do I fix it? I really want to try KDE as I've had better luck with it in the past.

I tried searching for this problem but the only useful suggestion that came up was to install Kubuntu (not Ubuntu) from scratch. I really want to avoid this. I thought changing desktops was supposed to be simple...

---

### Post by ianmillington on 2011-04-15
Hi and welcome

Log out of gnome and when you see the login screen at the bottom there will be a drop down menu that should enable you to pick kde.

HTH

Ian

---

### Post by Mercury048 on 2011-04-15
I know there is **supposed** to be such a thing, but I don't see it... that's the problem. Other threads I found on the topic just say to use the drop-down but I don't have one?

I'd attach a screenshot but I don't know how. (Help on that would be appreciated as well.)

---

### Post by 23dornot23d on 2011-04-15
to get the Full kde ...... do 

**sudo apt-get install kde-full**

and for the menu

**sudo apt-get install kdm**

then you will be able to select using the menu that comes up at login .... 
choose kdm when it asks you which desktop manager to use .........
click the blue square with the white arrow on it to get the menu of installed desktops

[IMG]http://img14.imageshack.us/img14/9494/menuzz.jpg[/IMG]

Once the login screen comes up you will be able to choose between Gnome or Kde Plasma

_______________________________________________________

if you dislike it and need to return back to the gdm login

sudo apt-get remove kdm

and choose gdm when it asks you .......

---

### Post by ankspo71 on 2011-04-16
> **Mercury048 said:**
> I know there is **supposed** to be such a thing, but I don't see it... that's the problem. Other threads I found on the topic just say to use the drop-down but I don't have one?

I'd attach a screenshot but I don't know how. (Help on that would be appreciated as well.)

Hi,
The sessions menu (the menu that lets you choose the desktop to log into) will appear after you click on your username in Ubuntu's purple login window (GDM). So log out of Ubuntu, click on your username in the login window, go to the bottom of the screen, choose the desktop you want to log into, then enter your password by your username in the login window, and proceed to login.

Kubuntu's blue login window (KDM) will always show the session menu, except for maybe the first time where no username has been typed into the userlist yet. So after you type your username for the first time, you should always see the session menu choices.

Hope this helps.

---

### Post by t2kburl on 2011-04-16
Another reason you may not see it is that you have automatic login enabled. If so, disable it (in your user account settings)temporarily to get the login menu after you reboot. Or just log out instead of rebooting.

---

### Post by Mercury048 on 2011-04-17
> **ankspo71 said:**
> Kubuntu's blue login window (KDM) will always show the session menu, except for maybe the first time where no username has been typed into the userlist yet. So after you type your username for the first time, you should always see the session menu choices.

Hope this helps.
My login screen is not blue. The background is a purplish thing (though it has other colours). The login window in the center of the screen is light grey, and has a reddish ubuntu logo at the top. It logs in as soon as I click my username. There's also a light grey bar at the bottom of the screen.

I guess this isn't KDM? I checked Synaptic and I have kdm installed. I think it was one of the things that got installed when I chose kde-desktop.

---

### Post by Mercury048 on 2011-04-17
After reading some more I tried:

```
sudo dpkg-reconfigure kdm
```

and selected kdm. After a reboot, I got a screen with a single terminal window! Nothing else! No login screen. It was bizarre. I restarted again just to make sure it wasn't a fluke and the same thing happened.

I re-ran the command and selected gdm and now I'm back to a working system but I still have no way to log into KDE.

What is going on??

---

### Post by Mercury048 on 2011-04-17
> **Mercury048 said:**
> It logs in as soon as I click my username.
So this was my problem. A detail I forgot to mention - since I thought it was irrelevant - was that my account had no password. When I clicked my name it logged me in immediately. After setting a password, when I click my name it now prompts me to enter my password and it is **only** during this time that the desktop selection becomes available.

I went back and experimented a bit and it seems it is impossible to specify the desktop to log into for a password-less account. This is... really bad UI design. Whoever built the login screen made the classic developer error of ASSuming too much about the state of the system. :P

That having been said, I am lovin' KDE. :cool: Not only does it look very nice with a layout much more to my taste, but it magically eliminated a couple of mouse issues I was having while using GNOME.

---

