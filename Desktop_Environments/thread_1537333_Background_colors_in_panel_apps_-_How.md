---
title: "Background colors in panel apps - How ???"
date: 2010-07-23
forum: Desktop Environments
---

### Post by WinRiddance on 2010-07-23
Alright, this has been driving me bonkers for months now and I can't find the answer anywhere. I like the custom theme options with standard gnome just fine, plenty of adjustments that can be made, with only one adjustment missing which would create perfection (at least in my opinion).

How on earth is it possible to change the backgrounds of the "mini-panels" which are always grey by default? No matter which Theme I choose and customize, I can never get _the background color_ of the time/date applet, monitors, evolution, garbage can, and so on to change. I'd like to make all of the backgrounds transparent, not just the main panels that contain the other stuff. Is this even possible, and if so, how?

I'm assuming since all of those apps have the same default color that an adjustment "wherever" would then change those default colors on all of the applets (hopefully).
Bet others would be interested in this too. Thanks in advance to anyone who can help.

---

### Post by AlphaLexman on 2010-07-23
A screenshot might help, your problem seems a little vague, or at least **I** don't quite understand.

---

### Post by soravis on 2010-07-23
Something like this?
[ATTACH]164364[/ATTACH]

In my case, when I changing the panel properties, more precisely the panel background, and set it to a color and *full opacity*, the background color of the applets changes accordingly. But when i set the transparency below 100%, the applets go back to the system theme background, which is opaque.
I don't think i's a bug... It's simply not a feature :P

---

### Post by AlphaLexman on 2010-07-23
Right click on the panel, click properties, select background tab, modify the settings between (none, solid color -> color or style, and background image).

---

### Post by stinkeye on 2010-07-24
In your theme's gtkrc file search for panel
and look for a line that looks similar to
```
bg_pixmap[NORMAL] = "panel.png"
or
bg_pixmap[NORMAL] = "panel_bg.png"
```
Put a hash mark(#) in front of that line.

Your theme will be in ~/.themes or /usr/share/themes

If it's in /usr/share/themes you will need to edit as root.
```
gksu nautilus /usr/share/themes
```

Log out and Log in for changes to work.

---

### Post by WinRiddance on 2010-07-24
Alright, sorry if I wasn't able to explain it better before. What **sovaris** mentioned was already covered by my initial thread ... I have no problem adjusting panel properties, background colors, and/or transparency values. The problem is with the other apps which always have the same default color of dark grey. When you click on their properties there's nothing there, to adjust the background value. Maybe this partial screenshot will help ....

_[IMG]http://www.ubuntu.steinfein.org/panelcolors.jpg[/IMG]_

Starting with the upper left corner ... There's a panel on the left and on the top. I can make the panels themselves any color that I want, or even transparent, that's not a problem. I'd like to make all of the background of the panels **and within the panel apps** very dark blue.

Right now I have everything dark grey because I made the panel colors match the colors that I can't change, like the colors in the workspace changer ... the colors where you see the symbols for evolution, the garbage can, and so on. Those items are not part of the standard panels, but there has to be a way to edit those colors too (I hope) ???

When I added the 3 drawers next to the start symbol I was able to adjust those background colors just fine (black, dark red, dark blue). I don't like docky bars, tried 4 different ones so far, and prefer the panels instead ...if I could only figure out a way to make those other grey colors change as well.

**@stinkeye**
Thanks, but again, the panels themselves are not the problem. I need to know where to find the default colors for _those other apps that reside on_ those panels, apps like date, garbage can, workspace switcher ... because when I change themes they're either dark grey or light. Tried about 20 different themes so far .... :(

---

### Post by stinkeye on 2010-07-24
> @stinkeye
Thanks, but again, the panels themselves are not the problem. I need to know where to find the default colors for those other apps that reside on those panels, apps like date, garbage can, workspace switcher ... because when I change themes they're either dark grey or light. Tried about 20 different themes so far ....

I may be wrong but for me, what I gave changes the background image of the 
garbage bin, time/date to the same as your panel colour.

1st pic is of ambiance theme with panel color set to blue.
2nd pic is of ambiance theme with the altered gtkrc and panel color set to blue.

The workspace switcher won't change because it's not drawing a background.
It's using your theme to draw the colours of your different workspaces.

---

### Post by WinRiddance on 2010-07-24
@stinkeye

Okay, I gotcha now.
But will your suggestion also work for the second panel on the left, i.e. for the background of any open apps? If that panel was on the bottom those spaces would be much larger of course since every open app would have its own larger horizontal button. Do those button backgrounds of already open apps change with your suggestion too?
I can live with the workspace switcher if that's the only thing ... ;)
Thanks.

---

### Post by erikkwonke2 on 2010-07-24
wow i didnt know how much u can customise ubuntu. just reading this inspire me to move on from windows to ubunto

---

### Post by WinRiddance on 2010-07-24
> **erikkwonke2 said:**
> wow i didnt know how much u can customise ubuntu. just reading this inspire me to move on from windows to ubunto

Not only is it so much cooler than windows ... and free to boot ... but I was just recently helping a 75 year old senior who bought an HP Windows7 machine. I was helping her because she got completely exhasperated with all of the BS that would constantly pop up at any given time ... security warnings, updates, norton anti-virus, HP center messages, HP update messages, Windows messenger, and so on. She was about ready to give up computing altogether out of sheer frustration. And I can't blame her because even I found all of that Windows7, HP, and Norton crap entirely overbearing & annoying to the extreme.

Windows7 on a bundled PC has got to be the most user UNFRIENDLY environment that I have ever seen, for anyone who's never had a computer before. Now she's a happy camper with a super easy to use Ubuntu setup .... :D

---

### Post by lizzibet on 2010-07-24
ok, but how come i have no trash bin on my lubuntu?

---

### Post by WinRiddance on 2010-07-25
> **lizzibet said:**
> ok, but how come i have no trash bin on my lubuntu?

PLEASE USE THE FORUM CORRECTLY. Your question has nothing to do with the topic at hand. Nor does it have a lot to do with Ubuntu since you're using _**Lu**_buntu which has XFCE as opposed to Gnome panels. Please post questions individually where they belong without hijacking an existing thread which often causes a moderator to close such a thread. That's not good for anyone.

When you post your question select LUBUNTU from the selection menu and put something in the title line which pertains SPECIFICALLY to your problem i.e. "missing trash can in Lubuntu" which will greatly enhance the ability for others to help you.

If you delete your question above by using the edit button then I'll delete this answer and the thread will once again be as it should.

---

### Post by bornagainpenguin on 2010-08-01
> **stinkeye said:**
> In your theme's gtkrc file search for panel
and look for a line that looks similar to
```
bg_pixmap[NORMAL] = "panel.png"
or
bg_pixmap[NORMAL] = "panel_bg.png"
```
Put a hash mark(#) in front of that line.

Your theme will be in ~/.themes or /usr/share/themes

If it's in /usr/share/themes you will need to edit as root.
```
gksu nautilus /usr/share/themes
```

Log out and Log in for changes to work.

Man you have no idea how long I've been looking for a way to do this!  Sir, you rock!  Thanks!  :guitar:

--bornagainpenguin

---

