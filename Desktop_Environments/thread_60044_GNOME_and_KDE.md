---
title: "GNOME and KDE"
date: 2005-08-26
forum: Desktop Environments
---

### Post by myha on 2005-08-26
Hi!

Could someone please explaim me if it is possible to have both KDE and GNOME desktop installed, and select which desktop manager to run? Like on login write gdm for gnome and kdm for KDE and select which window manager to run?
And i would also like to know if i change the /etc/X11/default-display-manager  from /usr/bin/gdm   to  kde will it boot directly to selected manager?

Thanks,
Miha

---

### Post by Lord Illidan on 2005-08-26
You can just install kubuntu-desktop from Synaptic. When it has downloaded and begun installing, a terminal window will pop up from the installation screen and ask you to select from gdm, xdm or kdm. You can chose from the 3, all will boot to Gnome or KDE..

---

### Post by myha on 2005-08-26
Well thanks, I will try that..

Can you please tell me howto change default display manager later... If I select kde now and I want to switch back to gnome later, how do I do that? Also if I select KDE now and if I write gdm in virtual console will it start in gnome?
Is there any program that asks you on startup which manager would you like to use?

Thank you in advance,
Miha

---

### Post by Lord Illidan on 2005-08-26
No, no... There is no difference between gdm and kdm when it comes to this 1 thing.

If I have gdm, I can chose to run either a Gnome Session or a KDE session.

If I have kdm, I can do the same..

It involves just clicking on icons and buttons.

So you can go with gdm or kdm, there is no need to launch them from a terminal or something...

---

### Post by duffman25 on 2005-08-26
[QUOTE=myha]Well thanks, I will try that..

Can you please tell me howto change default display manager later... If I select kde now and I want to switch back to gnome later, how do I do that? Also if I select KDE now and if I write gdm in virtual console will it start in gnome?
Is there any program that asks you on startup which manager would you like to use?

Thank you in advance,
Miha[/QUOTE]

you can change the default login manager in /etc/X11/default-display-manager

---

### Post by myha on 2005-08-26
Thank you both very much... I think I get the picture now...
I also found [this](http://www.ubuntuforums.org/showthread.php?t=55855&page=1) thread with similar question...

I'm not sure I want to do this anymore since I'll obviously have problems if I want to remove KDE and all packages that comes with it (btw will all kde programs be included if i install kde desktop - like kubuntu - or i'll have to install it manually)...  :???: Because ubuntu is working perfect right now, I'm switching from windows because I really like ubuntu and linux and I have finally got almost everything working (exept irda and graphic driver) and I'm afraid if I install KDE ill mess things up...  :-? 

Thank you,
Miha

---

### Post by myha on 2005-08-26
Well, I decided to try anyway, so it did
```
apt-get install kubuntu-desktop
``` 
and i get the following error:
```
root@lx-mihap:/usr/bin # sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: amarok but it is not going to be installed
E: Broken packages
``` 
 :neutral:

---

### Post by myha on 2005-08-26
ok, I got it worked, I installed amarok manually and everything is ok now!

Just one question more:
If i do apt-get install kubuntu-desktop i get a list of all libs and packages that will be installed... If I save the output and i leter decide to remove kde later and i do remove and add all packages will this do any damage to gnome?

---

### Post by exile on 2005-08-26
I should be safe to remove kde without affecting gnome. Uninstalling kde may also uninstall the kde apps, so they would go but gnome should stay mostly untouched.

I just want to add that in linux it doesn't have to be a either/or situation, you can have kde and gnome installed at the same time coexisting quite happily. I have both installed because I like some kde apps (k3b) and some gnome apps (evolution).

If you wanted to uninstall kde but still keep a kde app then you can try to install the app by itself and it should install only the base kde libraries needed to run the app.

If disk space is not a consideration I would recommend installing a few window managers and trying them out over an extended period of time to find out what suits you best.

Enjoy.

---

