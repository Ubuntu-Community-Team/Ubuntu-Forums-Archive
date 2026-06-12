---
title: "Changing GDE Theme From Command Line"
date: 2007-01-26
forum: Desktop Environments
---

### Post by Tsen on 2007-01-26
Man, I've been having tons of troubles today.  When it rains it pours, I guess.
Anyway, I installed a new icon set earlier.  I don't remember exactly what the name was, but it was one of the top rated ones over at Gnome Looks.  
Long story short, I was changing my theme to use some of the new looks I'd installed.  I was under the Theme Details/Controls section, arrowing down to preview all of the ones I had installed to find one that would look best with my wallpaper.
When I selected one of the new themes, everything crashed.  I rebooted, but every time it freezes before reaching the desktop.
So the problem is probably that the computer's trying to use a corrupted theme and can't load the desktop environment.  I can boot in safe mode or using the Live CD, but all attempts at a normal boot or one in safe graphics mode fail.
So, is there a way to change, disable or otherwise alter the theme or desktop environment from the command line in safe mode?
If possible, I'd like to just change the theme and leave everything else be, but if that's not possible, how would I go about reinstalling GDE, and would that help?

---

### Post by Tsen on 2007-01-26
Alright, well, no answers yet but it has only been a few minutes.
Well, I've been looking around for possible solutions.
Using only the command line in the safe mode, could I install KDE and set it as default?
For example, I was reading on installing KDE onto a standard Ubuntu installation over GDE.  
```
aptitude update
aptitude install kubuntu-desktop
```
Would this work alone in the command prompt?  The instructions later said you'd have to back out to the login window to switch to the KDE desktop, though, and since I'm doing this in command line I can't do that.  Also, I enabled auto-login, so I can't do that anyway.

---

### Post by ButteBlues on 2007-01-26
> **Tsen said:**
> Alright, well, no answers yet but it has only been a few minutes.
Well, I've been looking around for possible solutions.
Using only the command line in the safe mode, could I install KDE and set it as default?
For example, I was reading on installing KDE onto a standard Ubuntu installation over GDE.  
```
aptitude update
aptitude install kubuntu-desktop
```
Would this work alone in the command prompt?  The instructions later said you'd have to back out to the login window to switch to the KDE desktop, though, and since I'm doing this in command line I can't do that.  Also, I enabled auto-login, so I can't do that anyway.
```
nano ~/.gtkrc-1.2-gnome2
```

Edit as required.

---

### Post by Tsen on 2007-01-26
I'm a bit new at this.  I tried the command, and it worked, but I don't know where to go from there.  What do I edit, and how?  There's a blank text field, but I don't know what to put there.

---

