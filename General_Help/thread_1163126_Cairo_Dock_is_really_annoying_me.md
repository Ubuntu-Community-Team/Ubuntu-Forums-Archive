---
title: "Cairo Dock is really annoying me"
date: 2009-05-18
forum: General Help
---

### Post by Volt9000 on 2009-05-18
I'm having big problems with Cairo Dock.

I'm trying to configure it, but sometimes what would happen, for no apparent reason, is that when I re-enter the configuration dialog, it won't show up-- then if I try again to re-enter it, a small blank window will appear with nothing in it. At this point I have no choice but to shut down and restart Cairo Dock. When it restarts, all the customizations I did to it are gone, despite my having saved the theme!

This is making things EXTREMELY frustrating, as now this means I have to do everything ALL OVER AGAIN.

Am I missing something here, or is Cairo Dock really this buggy?

---

### Post by Volt9000 on 2009-05-18
Ok, well I found a temporary solution at least-- to go into .config/cairo-dock, delete the current_theme directory, them copy over my saved theme directory and rename it current_theme.

Strange, I thought that by selecting the saved theme this should happen automatically, but apparently it doesn't...

---

### Post by fabounet on 2009-05-19
if you saved your theme, you can restore it (don't forget to tick the 2 checkbox below, so that you recover your behavior and your launcher too !)

how did it happen ? are you able to reproduce it ?

---

### Post by qjmoss on 2009-05-19
Have you tried avant window navigator

---

### Post by squee on 2009-05-19
or gnome-Do?

---

### Post by Volt9000 on 2009-05-19
> **fabounet said:**
> if you saved your theme, you can restore it (don't forget to tick the 2 checkbox below, so that you recover your behavior and your launcher too !)

how did it happen ? are you able to reproduce it ?

That's the problem-- when this problem happens, if I try to restore it, it doesn't work. It just restores the default theme.
I can't reproduce it on demand, and it seems to happen randomly. I'll try running it from the command-line to see if I get any error messages.

> **qjmoss said:**
> Have you tried avant window navigator
> **squee said:**
> or gnome-Do?

No, I want to use Cairo Dock specifically because it looks nice, and I like the OSX-like effects.

---

### Post by qjmoss on 2009-05-20
> **Volt9000 said:**
> That's the problem-- when this problem happens, if I try to restore it, it doesn't work. It just restores the default theme.
I can't reproduce it on demand, and it seems to happen randomly. I'll try running it from the command-line to see if I get any error messages.




No, I want to use Cairo Dock specifically because it looks nice, and I like the OSX-like effects.

Well, I'm never messed with Cairo dock, but I would like to let you know...

That avant window navigator has different themes, and it is also customizable.

I believe there are, stacks or whatever osx calls that little effect that sold their new os.

---

### Post by fabounet on 2009-05-20
you should try CD2, you would see the difference ;-)

you can try the following : 
be sure to have the last version (currently 2.0.2, it changes often)
run cairo-dock -l debug -o
then if it happens again, the last lines may help to find an answer.
I would have said it's a rights issue, but if it works sometime, then it can't be.

---

