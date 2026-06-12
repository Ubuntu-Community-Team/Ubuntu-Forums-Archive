---
title: "Panel not at bottom of screen (KDE 4.0)"
date: 2008-04-25
forum: Desktop Environments
---

### Post by xArv3nx on 2008-04-25
Hii!

I recently did a fresh install of Kubuntu KDE 4.0, and whenever I start the session, the Panel isn't at the very bottom, even though it's SUPPOSED to be.

How would I go about fixing this? Screenshot is attached. :)

---

### Post by natman on 2008-04-25
This is just me thinking out loud but, perhaps try turning off all desktop effects and log out and in?
Also try adjusting the screen res, to see if anything changes
If that fails log out and log in in safe mode ( termina ) and Delete the .kde4 directory - [COLOR="Red"]this will delete any settings you have defined and restore kde to out of the box.[/COLOR]
[HTML]rm -r ./.kde4[/HTML]

---

### Post by xArv3nx on 2008-04-25
> **natman said:**
> This is just me thinking out loud but, perhaps try turning off all desktop effects and log out and in?
Also try adjusting the screen res, to see if anything changes
If that fails log out and log in in safe mode ( termina ) and Delete the .kde4 directory - [COLOR="Red"]this will delete any settings you have defined and restore kde to out of the box.[/COLOR]
[HTML]rm -r ./.kde4[/HTML]
I think it's a resolution bug.

If I go to "Display" (System Settings), it changes the resolution to 1024x768 (or something small), and it also has something weird on the screen part, such as "TMDS-1".

I think what's happening is KDE 4.0 is detecting two screens (WTF? I only have one) and showing them on one screen (both on the same desktop).

It makes sense, but how would I fix this?

---

### Post by natman on 2008-04-25
Im guessing if your hunch is right you will have to edit xorg.conf, unfortunately thats out of m leauge.
Perhaps try posting over in Beginners better chance of an expert seeing you there.
Sorry cant help more. How are you finding the KDE4 desktop, ie lack of icons that arent widgets?

---

### Post by xArv3nx on 2008-04-25
> **natman said:**
> Im guessing if your hunch is right you will have to edit xorg.conf, unfortunately thats out of m leauge.
Perhaps try posting over in Beginners better chance of an expert seeing you there.
Sorry cant help more. How are you finding the KDE4 desktop, ie lack of icons that arent widgets?
xorg.conf is fine, this only happens on KDE 4.0 (this also happened on OpenSUSE with KDE 4.0).

What do you mean?

---

### Post by natman on 2008-04-25
The fact that icons on the Desktop, when drag'd dont drop into folders and when right clicked dont give any file options.

---

### Post by xArv3nx on 2008-04-26
It appears that other people are having the exact same issue as me (confirmed bug reports all over the place).

Does anyone have a fix?

---

### Post by Jowi-real on 2008-10-22
> **xArv3nx said:**
> Hii!

I recently did a fresh install of Kubuntu KDE 4.0, and whenever I start the session, the Panel isn't at the very bottom, even though it's SUPPOSED to be.

How would I go about fixing this? Screenshot is attached. :)

I had the exact same problem. With all desktop environments. I tried with XFCE, KDE4, stand alone compiz as well. 

I am using the "intel" driver and I have a 945GM chipset (mac mini).

"xrandr -q" showed VGA with correct resolution and something called TMDS-1 with wrong resolution (It shouldn't even exist since I don't even have a second monitor).

"xrandr --output TMDS-1 --off" didn't change a thing.

I found a solution - Deactivate TMDS-1!

In /etc/X11/xorg.conf add the following monitor after the first one:

Section "Monitor"
        Identifier      "TMDS-1"
        Option          "Ignore"        "true"
EndSection

Restart X (Ctrl-Alt-Backspace should do it)

 - This is similar to [http://ubuntuforums.org/showthread.php?t=716031](http://ubuntuforums.org/showthread.php?t=716031) but that thread is closed so I can't post a reply there -

---

