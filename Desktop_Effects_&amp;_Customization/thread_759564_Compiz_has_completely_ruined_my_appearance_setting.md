---
title: "Compiz has completely ruined my appearance settings..."
date: 2008-04-19
forum: Desktop Effects &amp; Customization
---

### Post by MedellinManDem on 2008-04-19
After this was installed, at first things were going well, then I changed a few things around and uninstalled it eventually. Now, my windows are too big for my resolution, I can't see any borders, and I can't seem to change anything. I'm seriously thinking of going back to XP now...

Does anyone have any idea about what to do?

---

### Post by Zorael on 2008-04-19
Enter the following in a run box (Alt+F2) to get your borders and titlebars back.
```
metacity --replace
```

As for your windows being too big for your resolution; curious. And you're sure this is merely not your windows lacking titlebars, and as such look as if they're extending outside the screen limits? If they *are* outside the limits, once you have Metacity running, hold Alt and drag the window to move it to a point where you can handle it.

To set up Compiz, if you want to give it another go, I recommend you don't use the Advanced Desktop Effects menu and instead install CompizConfig Settings Manager (CCSM; package name **compizconfig-settings-manager**). In there, just make sure to export your profile every now and then (under Preferences), so if you botch something up you can always import it back.

And again, run the metacity command if things become unmanageable. Make that '**kwin --replace**' if you're running KDE.


edit: To explain, you missing borders and titlebars would be either because your window decorator isn't working or isn't started. As the name implies, window decorators draw borders and titlebars on windows. None such running could be either due to you missing certain options in your xorg.conf file (**/etc/X11/xorg.conf**), or that you haven't enabled the Window Decorations plugin in CCSM. Nvidia cards, for instance, require that you add some lines to get stuff working properly. From the top of my head, AllowGLXWithComposite and AddARGBGLXVisuals.

---

### Post by tedt on 2008-04-19
Simplest answer is go back to non-compiz

Hit Alt-F2

in the dialog box enter

metacity --replace

To fix your compiz problems you will need to be more specific.

The one thing I can think of right now is to open up synaptic and reinstall he compiz packages

---

### Post by itix on 2008-04-19
What!?
You have to explain exactly what is wrong and the background and what exactly that you did.
We don't stand behind your back so we don't know exactly what you have done.

---

### Post by MedellinManDem on 2008-04-19
RIght, well I got the window borders back somehow without the metacity command, so thank you both for that. Is there any way to modify the window borders so they aren't as big?

---

### Post by MedellinManDem on 2008-04-19
> **itix said:**
> What!?
You have to explain exactly what is wrong and the background and what exactly that you did.
We don't stand behind your back so we don't know exactly what you have done.

Well the other two posters seemed to post valid commands to return to default, which is essentially what I was looking for.

---

### Post by Zorael on 2008-04-19
> **MedellinManDem said:**
> RIght, well I got the window borders back somehow without the metacity command, so thank you both for that. Is there any way to modify the window borders so they aren't as big?
Change your theme. :>

---

### Post by itix on 2008-04-19
Ok, great. If you dare try compiz again, type *compiz --replace*.
Also, mark the thread as solved if it solved your problems completely. You might want to turn the compiz settings of in the *system =>appearence => visual effects* and choose none. Otherwise your problem will return when you log back in.

---

### Post by MedellinManDem on 2008-04-19
Compiz has been removed from my system. :)

---

### Post by MedellinManDem on 2008-04-19
I must say, at the moment it looks as though I'm viewing Ubuntu through an 800x600 resolution...I don't know if it's the font or what.

---

### Post by Zorael on 2008-04-19
It's okay, we know you'll succumb eventually.

Time is on our side.

edit: As for the resolution, what does the Screen Resolution app say? Compiz shouldn't tinker with your available resolutions.

---

### Post by MedellinManDem on 2008-04-19
It says 1200 x 800.

I'm using the human theme.

---

### Post by itix on 2008-04-19
That's even better =p
The resolution (which I presume that you have checked) can be changed at *system => preferances => screen resolution*.

It might be your theme or it might be the DPI. I had a problem with my dpi with certain live CDs prevoisly. I can see if I can find that threa for you => brb.

---

### Post by itix on 2008-04-19
Ok, judging from your post, I'd say its the DPI. Is the font large everywhere??

---

### Post by itix on 2008-04-19
Try this (in terminal) and then log out and log back in:
```

echo "Xft.dpi: 100" > ~/.Xdefaults
xrdb -merge ~/.Xdefaults
```

If it says: "no permission", just add a sudo before the line and enter your password. Your password won't be visible when you type it in. That's normal for terminal passwords.

---

### Post by MedellinManDem on 2008-04-19
It's ok, I've just installed openbox, which immediately looks far more suited to my needs.

Thanks for all the help guys.

PS It was the dpi, but it was still too big!

---

### Post by itix on 2008-04-19
Just change the value :p
You can just change it from where it says 100 to something like 75 or 50 or what feels best.

---

