---
title: "KDE environment"
date: 2007-08-15
forum: Desktop Environments
---

### Post by durfff on 2007-08-15
Yo everyone, 

I have a couple of questions for you... I was using Ubuntu for a while and decided to give kubuntu a go, and I'm not disappointed, it rocks, really. Yay. 

However, here's a couple of things I've not figured out yet...

- Let's start with what (I assume) must have a simple answer: how do I change the prefs so I have to double-click to open files? I guess the single click is set by default, but is it something I can change? I've looked around in the preference panel but not found anything :(

- Weirder thing, but there must be an answer: all my icons are black and white! On the desktop and in Konqueror, the icons are all black and white (even pictures and such). I'm using the Ubuntu default theme on my machine, but no glorious orange, just black and white, thought it was a bit weird. And even weirder when I realised ONE icon had color: it's an icon for a wine app... Any help on this malarkey???

Cheers!

Fred

---

### Post by GeneralZod on 2007-08-15
> **durfff said:**
> 
- Let's start with what (I assume) must have a simple answer: how do I change the prefs so I have to double-click to open files? I guess the single click is set by default, but is it something I can change? I've looked around in the preference panel but not found anything :(


This always stumps everybody - it's in a really unintuitive place :/

Anyway, it's in the "Mouse" portion of System Settings.

> 
- Weirder thing, but there must be an answer: all my icons are black and white! On the desktop and in Konqueror, the icons are all black and white (even pictures and such). I'm using the Ubuntu default theme on my machine, but no glorious orange, just black and white, thought it was a bit weird. And even weirder when I realised ONE icon had color: it's an icon for a wine app... Any help on this malarkey???


Now this is interesting! Can we see a screenshot?

Edit:

If I were to guess: can you type

```

kcmshell icons

```

at the command-line, click Advanced, select Desktop/ File Manager, and see if the "Default" icons are coloured?

---

### Post by ComplexNumber on 2007-08-15
> - Weirder thing, but there must be an answer: all my icons are black and white! On the desktop and in Konqueror, the icons are all black and white (even pictures and such). I'm using the Ubuntu default theme on my machine, but no glorious orange, just black and white, thought it was a bit weird. And even weirder when I realised ONE icon had color: it's an icon for a wine app... Any help on this malarkey???
which icon theme is selected in  the kde control centre?

---

### Post by durfff on 2007-08-16
Yo, thanks for the quick replies! Got the single/double click sorted, thanks for that! 

As for the icons, here's what i've got: screenshot 1 shows you my desktop with all icons b&w and that one little wine app with red... odd, isn't it! The second screen shot is a bit weird as well: you can see that the default icons appear partly coloured in the configuration utility: the folder looks orange, but the default app icon (on the left) is greyed out when really it should be blue, is that right? Yet the folders still are grey...

Very confused :(

edit: I thought I'd post that in aonther forum but as you can see in Konsole, it gives me an error message whatever the request I make, same error message but then goes through and does the request normally... Could this be linked?

---

### Post by Happy_Man on 2007-08-16
No, the Konsole error is normal. It happens every time you launch a GUI. Perfectly harmless, just a quirk of Kubuntu. 

Now, the icons may just be like that in that theme on KDE, or perhaps you..... wait.... I see! Having just opened that up myself, yes, the Human theme for me only applies the folders, everything else just follows the last KDE icon theme I had. Perhaps that helps?

---

### Post by igknighted on 2007-08-16
Is your background intentionally B&W?  That looks like the stock Kubuntu wallpaper, but it should be light blue...  I've never seen anything like this.  It's like KDE forgot how to draw colors (at least for the pieces it has direct control of)

---

### Post by Prefader on 2007-08-16
Re: the errors you're seeing, check your Xorg.conf for stuff about wacom tablets.  Unless you've got a tablet, you can remove the sections and lines (make sure to remove ALL references to these devices, otherwise the X server will fail to start and you'll be left without a GUI) referring to the tablet and stylus, and the errors will clear up.  You're seeing the errors because your X server is configured for devices that aren't present on your system.

In fact, just out of curiosity, can you post your xorg.conf, as well as your Xorg.0.log?  I wonder if there's something funky going on there.

---

### Post by durfff on 2007-08-17
[QUOTE=Happy_Man]Now, the icons may just be like that in that theme on KDE, or perhaps you..... wait.... I see! Having just opened that up myself, yes, the Human theme for me only applies the folders, everything else just follows the last KDE icon theme I had. Perhaps that helps?[/QUOTE] I'll give that a go and see what happens...

[QUOTE=igknighted]Is your background intentionally B&W? That looks like the stock Kubuntu wallpaper, but it should be light blue... I've never seen anything like this.[/QUOTE]
Ha sorry, should have said... Yeah it's actually the default Ubuntu background but I like a dark background so tweaked it a bit... Colour backgrounds work though, no problem. 


[QUOTE=Prefader]Re: the errors you're seeing, check your Xorg.conf for stuff about wacom tablets. Unless you've got a tablet, you can remove the sections and lines (make sure to remove ALL references to these devices, otherwise the X server will fail to start and you'll be left without a GUI) referring to the tablet and stylus, and the errors will clear up. You're seeing the errors because your X server is configured for devices that aren't present on your system.[/QUOTE]
I noticed that actually when I switched to Kubuuntu I had to redo my xorg.conf for my ATI card and saw all them entries... I just left the there not sure what they were for, I'll try to remove them. I'll see what happens if I change to another icon set and back, if nothing good I'll post xorg stuff.
 

Cheers for all the replies!!!

---

### Post by durfff on 2007-08-18
well I tried to change the icon set and no colour... So I changed back to Ubuntu default to see if colour would come back and no luck... But I rebooted this morning and colour is back! Ace, it was probably a case of having to restart the X-server for it to work properly, even though it says it's updating the configuration...

Anyways back with colours now :)

---

