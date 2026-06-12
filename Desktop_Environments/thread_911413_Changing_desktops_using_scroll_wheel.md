---
title: "Changing desktops using scroll wheel"
date: 2008-09-05
forum: Desktop Environments
---

### Post by benerivo on 2008-09-05
Is there a setting that allows me to change desktops (go from desktop 1 to desktop 2) using the mouse scroll wheel, whilst the cursor is anywhere on the desktop background. I'm not using compiz and i wouldn't like to always have to move the cursor over to the pager on the panel. It's the main thing i liked from trying out fluxbox and openbox.

---

### Post by benerivo on 2008-09-06
**bumped**.

I didn't think this was possible, but i've bumped just in case.

---

### Post by ad_267 on 2008-09-06
I've subscribed just in case it's possible too, but I think this only works with Compiz.

---

### Post by ronnielsen1 on 2008-09-06
> Is there a setting that allows me to change desktops (go from desktop 1 to desktop 2) using the mouse scroll wheel, whilst the cursor is anywhere on the desktop background.
Now if your mouse is over the desktop pagers it will do that

---

### Post by breaddawson on 2008-09-06
Hi, actually i'm always changing desktops like this, but not only by mouse wheels, I bind Ctrl+Alt+Mouse Wheels.

What i did is modify the settings in 

Compiz -> Desktop Wall -> Bindings -> Move within Wall

Then i bind "Move Next" to Ctrl-Alt-Button5 which is wheel down
and "Move Prev" to Ctrl-Alt-Button4 which is wheel up

Hope these help

---

### Post by ZeldaFan on 2008-09-06
> **breaddawson said:**
> Hi, actually i'm always changing desktops like this, but not only by mouse wheels, I bind Ctrl+Alt+Mouse Wheels.

What i did is modify the settings in 

Compiz -> Desktop Wall -> Bindings -> Move within Wall

Then i bind "Move Next" to Ctrl-Alt-Button5 which is wheel down
and "Move Prev" to Ctrl-Alt-Button4 which is wheel up

Hope these help

I dont think he wanted to use compiz, but GTK instead (standard gnome). Here's how:
Go to system -> preferences -> keyboard shortcuts
Scroll down until you see "Move one workspace to the left" and "Move workspace to the right". You can change the keyboard shortcut, but you may also be able to assign a mouse shortcut as well, I'm not completely sure.

---

### Post by benerivo on 2008-09-06
> **ZeldaFan said:**
> Go to system -> preferences -> keyboard shortcuts
Scroll down until you see "Move one workspace to the left" and "Move workspace to the right". You can change the keyboard shortcut, but you may also be able to assign a mouse shortcut as well, I'm not completely sure.Thanks for the tip ZeldaFan, but this does only allow keyboard shortcuts.

---

### Post by alfu on 2010-01-07
In 9.04 on my Toshiba laptop, scrollwheel on the background would swap workspaces, but in 9.1 it no longer does this.

I wish it could -- it was a nice feature in Ubuntu, that I used to use when showing off the O/S to prospective adopters.

---

### Post by MooPi on 2010-01-07
That feature is standard with Openbox. Another way of getting this feature is to enable Compiz.

---

### Post by LuisGMarine on 2010-01-07
I have compiz and Ubuntu 9.10 and I just found out my scroll doesn't work anymore >.< uh oh!

---

### Post by ad_267 on 2010-01-08
> **LuisGMarine said:**
> I have compiz and Ubuntu 9.10 and I just found out my scroll doesn't work anymore >.< uh oh!

I think the setting was disabled in 9.10 because it was too easy to do accidentally and some people wouldn't know what happened when they accidentally changed workspace. Just enable it again from the Compiz Config Settings Manager. It's in there somewhere.

---

### Post by stinkeye on 2010-01-08
Viewport switcher

---

### Post by LuisGMarine on 2010-01-08
cool thanks I think that I need to go out and try it!

---

### Post by monikgtr on 2010-01-12
> **stinkeye said:**
> Viewport switcher
I wanted to fix that too! Thanks! That config in Viewport Switcher fixed it :D

(on Ubuntu Karmic)

---

### Post by LuisGMarine on 2010-01-12
I found out that if I just hoover over my gnome-docky workspace plugin and due the scroll wheel switch it works.  Also I've enabled some options to rotate my desktop with clicking and holding the scroll wheel while I move left or right into a new desktop. Gives me like a flipping a picture effect.  Pretty neat stuff.

---

### Post by stinkeye on 2010-01-12
> **LuisGMarine said:**
> I found out that if I just hoover over my gnome-docky workspace plugin and due the scroll wheel switch it works.  Also I've enabled some options to rotate my desktop with clicking and holding the scroll wheel while I move left or right into a new desktop. Gives me like a flipping a picture effect.  Pretty neat stuff.
You might like [_**[COLOR="DarkRed"]easystroke[/COLOR]**_]("http://sourceforge.net/projects/easystroke/files/") a mouse gestures program. plenty of options for making custom shortcuts.
[COLOR="#8b0000"]Tip:[/COLOR]Change the gesture button to button 3.
Set a downstroke gesture to the End key and an upstroke gesture to the Home key 
to easily navigate forum pages.

---

