---
title: "Help with XFCE transparency tweaking"
date: 2007-03-01
forum: Desktop Environments
---

### Post by raul_ on 2007-03-01
Hello fellow Ubuntu-ers (i felt like saying this). I'm trying XFCE (from Gnome) and i really like it, but i MUST ask this. I can't enable transparency =\ In Gnome I turned Beryl on and the terminal was transparent and blablabla. In XFCE i turned on Beryl, and the terminal is still fake transparent. So i thought to myself that XFCE isn't Gnome and started browsing and reading. 

It seems that I can enable the composite extension and tweak those transparency settings and make XFCE look all pretty. Which leads me to the first question:

**Is this really necessary, or I can achieve this with Beryl and i'm missing something?**

And question number two:
[B]
Why can't I enable composite?[/B]

I edited my xorg.conf and enabled the composite extension like this:

```

Section "Extensions"
        Option "Composite" "true"
EndSection

```

i tried both a X restart and a complete reboot and the "Composite" tab in the Window Manager tweaks just doesn't appear.

Just so you guys have an idea, this is what I pretend:

[Click on the pictures on the page to enlarge]("http://zimirk.wordpress.com/2007/02/17/an-evaluation-of-xubuntu/")

If I can achieve this, I think i'm going Xubuntu all the way :)

---

### Post by raul_ on 2007-03-02
One more thing, i installed xfce with "sudo aptitude install xubuntu-desktop". Does this version even have a built-in composite manager, or was it compiled without composite support?

---

### Post by abstrustication on 2007-03-02
You need to edit ~/.config/xfce4/mcs_settings/wmtweaks.xml.

Change the value field of the line that contains "UseCompositing" so that value="1".

---

### Post by kerry_s on 2007-03-02
Update to the latest xfce4-> [http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy](http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy)
composite works in that.

---

### Post by raul_ on 2007-03-02
> **abstrustication said:**
> You need to edit ~/.config/xfce4/mcs_settings/wmtweaks.xml.

Change the value field of the line that contains "UseCompositing" so that value="1".

you're my hero :)

Too bad the settings don't stay when i change to beryl...

Is it possible to enable transparency in inactive windows with beryl? Xfce is really fast but i miss my wobbly windows :popcorn:

EDIT: stupid question. Trail Focus does that. I'm really liking this right click menu thingy :mrgreen: They should implement this on Gnome. It's so functional

---

### Post by alalor1 on 2007-03-19
I can't find a wmtweaks.xml file in my computer.  I searched everywhere and everyway.
Can it have some other name?
I managed to find how to make the terminal window transparent, but nothing else.
Also, Thunar if opened from the menu looks regular, if opened from the terminal window with the command line, has a cool black face.
Thank you

---

### Post by andycyca on 2007-04-16
> **alalor1 said:**
> I can't find a wmtweaks.xml file in my computer.  I searched everywhere and everyway.
Can it have some other name?
I managed to find how to make the terminal window transparent, but nothing else.
Also, Thunar if opened from the menu looks regular, if opened from the terminal window with the command line, has a cool black face.
Thank you

I think wmtweaks.xml is in home/your_username/.config/mcsettings
-------------------

---

### Post by FuturePilot on 2007-04-16
> **alalor1 said:**
> I can't find a wmtweaks.xml file in my computer.  I searched everywhere and everyway.
Can it have some other name?
I managed to find how to make the terminal window transparent, but nothing else.
Also, Thunar if opened from the menu looks regular, if opened from the terminal window with the command line, has a cool black face.
Thank you
You have to open the Window Manager Tweaks menu and change some settings change them back to how they were before. Then close it. It should generate the .xml file.

---

### Post by mrazster on 2007-04-16
As said before..there are settings for both transparency and composite in xfwm. Go to: menu / settings / window manager tweaks / compositor. 
And just enable it. Don't have to anything else..

---

### Post by FuturePilot on 2007-04-16
> **mrazster said:**
> As said before..there are settings for both transparency and composite in xfwm. Go to: menu / settings / window manager tweaks / compositor. 
And just enable it. Don't have to anything else..
In some cases you do have to do something else. For some people the tab for Compositing does not exist unless you edit the .xml file.

---

### Post by mrazster on 2007-04-17
> **FuturePilot said:**
> In some cases you do have to do something else. For some people the tab for Compositing does not exist unless you edit the .xml file.

OK...it might so. Won't argue...you seeme to be more experienced than me. 
But it has worked for me in Dapper, Edgy and now Fiesty...all clean xubuntu installs.

---

