---
title: "autostart programs in lubuntu for absolute beginners"
date: 2012-05-22
forum: Desktop Environments
---

### Post by Tjampman on 2012-05-22
Hi
How do I make e.g. empathy autostart on login in Lubuntu 12.04?
Apparently it is well documented, [http://wiki.lxde.org/en/LXSession#Automatically_start_some_applications_on_login](http://wiki.lxde.org/en/LXSession#Automatically_start_some_applications_on_login)

>  Put *.desktop files of those applications in ~/.config/autostart, and they will get executed when the session starts.

But apparently I'm a moron because I still don't get it... What's a .desktop file and where do I find them? I looked through the /usr/bin folder where I usually find installed apps not showing anywhere else, but there is no hidden files there.

Please, could somebody please explain it to me as they would to a 3 year old. Thanks.

---

### Post by cortman on 2012-05-22
It's very simple. There's a file deep in your home folder called "autostart". You simply add a line to that file that says "@program_nmae", to make it startup.
Open a terminal and run

```
leafpad ~/.config/lxsession/LXDE/autostart
```

This will open the autostart file in a text editor. Simply add the line

```
@empathy
```

Save and close. Upon reboot empathy should start right up.

---

### Post by Tjampman on 2012-05-22
that didn't seem to work...

Here is what I did:
From the terminal 
```
leafpad ~/.config/lxsession/LXDE/autostart
```
I wrote in @empathy as you said, and saved, but since there were since the folder did not exist I saved the file as autostart

I didn't work so I tried copy and pasting the file into /home/.config/autostart/
but that didn't work either.


I just found another page/tutorial on the net (and now I cannot refind it) where they mention to **copy the file from /usr/share/applications in to /home/.config/autostart** and that seems to work fine, I just logged out/in and empathy is starting up automatically, now.

---

### Post by MG&amp;TL on 2012-05-22
For future reference, sometimes programs don't have a .desktop.

```
mkdir -p ~/.config/lxsession/LXDE/
touch ~/.config/lxsession/LXDE/autostart
leafpad ~/.config/lxsession/LXDE/autostart
```

Should work. I imagine it got saved in the wrong place last time.

---

### Post by Lyfang on 2012-10-20
Add your startup applications in Lubuntu 12.10 like this:
1. Go to /home/USERNAME
2.  Press Ctrl+h
3. Go to /home/USERNAME/.config
4. Create the folder autostart
5. Go to the menu > right-click > add to desktop
6. Move shortcut to /home/USERNAME/.config/autostart
7. Restart Lubuntu
See also: [http://wiki.lxde.org/en/Autostart](http://wiki.lxde.org/en/Autostart)

---

### Post by inearlygaveup on 2012-11-16
> **Lyfang said:**
> Add your startup applications in Lubuntu 12.10 like this:
1. Go to /home/USERNAME
2.  Press Ctrl+h
3. Go to /home/USERNAME/.config
4. Create the folder autostart
5. Go to the menu > right-click > add to desktop
6. Move shortcut to /home/USERNAME/.config/autostart
7. Restart Lubuntu
See also: [http://wiki.lxde.org/en/Autostart](http://wiki.lxde.org/en/Autostart)

Thanks Lyfang - my autostart folder was already there, just didn't know where to find it.

I needed to add "Redshift" to my startup as I had been starting it manually (for ages)since moving to Lubuntu from Ubuntu.
Thanks again

---

### Post by kokoshmusun on 2013-01-19
I was unable to get redshift to work with this method. It doesn't work at all and I've learned that it's because it relies on gnome-clock for something.  So I need to not just run redshift, but to run this command: redshift -l lat:lon (my lattitude and longitude of course).  how do I add this to startup?

---

### Post by inearlygaveup on 2013-01-20
There is probably an easier way than this but this is what I did and it worked.
I pasted a copy of the Redshift Icon onto my desktop opened /home/martin/.config/autostart dragged the Icon into the autostart folder saved and exited. 
BUT MAKE SURE you have added you Location Details mine was "gtk-redshift -l 53.48:1.33"

If its already in your autostart, you can add your location by right clicking the icon and opening with leafpad and adding the detail - mine is like

[Desktop Entry]
Version=1.0
Name=Redshift
GenericName=Color temperature adjustment
Comment=Color temperature adjustment tool
Exec=gtk-redshift -l 53.48:1.33
Icon=redshift
Terminal=false
Type=Application
Categories=Utility;
StartupNotify=true

It started on my next boot - hope this helps

---

### Post by wakari on 2013-01-24
Hi!

The "**sleep 20;transmission-gtk -m**" command work fine in command line. 
But not in the "**etc/xdg/lxsession/Lubuntu/autostart**" .

I would like to use this "primer" solution.
Cuold you help?
thx w

---

