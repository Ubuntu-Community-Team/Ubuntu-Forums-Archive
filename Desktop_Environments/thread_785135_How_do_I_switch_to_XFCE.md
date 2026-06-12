---
title: "How do I switch to XFCE??"
date: 2008-05-07
forum: Desktop Environments
---

### Post by enoughsaid05 on 2008-05-07
Hi all...am thinking whether if it is possible for me to install XFCE. I figured out that GNOME can be quite a resource hog to my computer (what can u expect from a 512mb ram with 2.0Gb AMD64 processor with only a 512kb cache??), so I wished to try out XFCE and see if it would be better. I don't want to uninstall GNOME though because I figured that 80GB is quite a lot. There are few questions:

1) How do I install XFCE.
2) How do I switch between GNOME and XFCE?

If I can select session upon login, does the preference remain till I change on my next login?

3) If I don't want XFCE, how do I uninstall?
4) Is installation/ uninstallation going to do much harm to my system? (i.e. GNOME clashes with XFCE

THANKS!!

---

### Post by agim on 2008-05-07
I am amazed that no one has answered your question yet.

To try xfce type this into a terminal

sudo apt-get install xubuntu-desktop

or find the package xubuntu-desktop in synaptic, if you prefer that method.

After its completely finished downloading and installing, log out. At the bottom left of the login screen will be a button that says Options. Click it, then click Sessions, and choose xfce. It should run very well on your resources.

Edit: To uninstall, you will have to keep track, or write down, all of the packages it installs, but its not a very big install. It won't take too much room.

And no, there won't be any problem with both XFCE and Gnome. I have had those and kde and several window managers at a time before.

---

### Post by Silent Warrior on 2008-05-07
Arr, foiled again!
(READ: What he/she/it said.)

I'll just add a few more things for clarity.

In my eperience, it seems that the default selected session-option is 'previous session', so if you log into XFCE and don't touch anything when you log in the next time, you should find yourself in XFCE yet again. So, um, be concentrated and mindful if you for whatever reason log into some failsafe session, ok? It will give you a longer life. Take my word for it.
3: Through Synaptic, or whatever else package-manager you use. Same as installing.
4: Quite unlikely. That is to say, it does depend on what state the package-version you select is in (look for 'preferred version' in Preferences or somesuch and set it to whichever setting floats your boat - 'stable' seems to be recommended), and the overall health of your hardware may have an impact, but other than that, if Synaptic finds a conflict, it won't install the offending packages. There is also the human factor, but I can't for the life of me imagine how far you have to sink to actually physically damage your system with a carefully controlled software-installation.
Should you want to uninstall either Gnome or XFCE, though - pay close attention to what packages are removed along with either. It isn't just a matter of merely replacing one type of 'start-menu' with another.

---

### Post by enoughsaid05 on 2008-05-07
"So, um, be concentrated and mindful if you for whatever reason log into some failsafe session, ok? It will give you a longer life. Take my word for it.
"

Why is it so?

---

### Post by enoughsaid05 on 2008-05-07
Ohoh another thing!!!!!

If my GNOME has applications like Open Office and Totem, will Xfce have them after I install XFCE?

---

### Post by Sef on 2008-05-07
> If my GNOME has applications like Open Office and Totem, will Xfce have them after I install XFCE?

Yes you will have them and Xubuntu's as well.

---

### Post by stream303 on 2008-05-07
If you want to get back to a "pure" xfce environment as if you had installed Xubuntu in the first place, there is a great cut-n-paste method of doing the hard work for you:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

That saved my sanity when I installed Gutsy from a magazine once, and it installed all three of the major desktops, Ubuntu/Kubuntu/Xubuntu - talk about overload :)

---

### Post by tattrat on 2008-05-07
I am in the process of doing the same thing, in fact I have tried it twice. 

The first time I installed all the relevant packages from package manager, and then rebooted. Fter reboot you get an Xubuntu style login screen. You can choose in "session" which seesion type you want, but remember to opt for xfce the first time, as the default is "last session".

Having booted, xfce starts, and looks just like xubuntu. I then checked everything was there and woorking, so then I rebooted. From this point xfce would not start. Gnome was fine.  So ithought perhaps I'll just reinstall (the whole system) all over and this time make no changes to appeance in the first boot of xfce. But I have the same problem. Xfce won't start, but gnome works just fine.

---

### Post by DaVince21 on 2008-05-07
Just a bit of info for you: you can have as many window managers installed as you want and switch between them in the Gnome (or KDE) login manager as much as you like. So once you install Xfce, you're free to run it from the login window as much as you like, and even set/unset as the default window manager...

Linux's flexible, innit? ;)

Oh yeah, one other note: in Ubuntu, Xfce takes over some settings from Gnome, but it won't interfere with any Gnome settings as far as I know. So you could safely remove it again if you don't like it.

---

### Post by DaVince21 on 2008-05-07
EDIT: damn, double post.

---

### Post by Silent Warrior on 2008-05-09
> **enoughsaid05 said:**
> Why is it so?

Well, if you forget you left Gnome (or whatever desktop) on Failsafe (sheesh, so I'm old, alright?), and come back to a REALLY slimmed desktop-environment... and all sorts of drivers and such aren't loaded, for example your network-card... you get nervous. Learn from my growing senility.

---

