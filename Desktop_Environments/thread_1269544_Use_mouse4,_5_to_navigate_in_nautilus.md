---
title: "Use mouse4, 5 to navigate in nautilus"
date: 2009-09-18
forum: Desktop Environments
---

### Post by Mitur on 2009-09-18
Ive just started using ubuntu on all my computers, mainly since i need it to be more compatible with the schools unix system.

But now when i have started using it i really love it! I only miss one small thing, the ability to navigate in nautilus with my mouse buttons.

It works great in ffox, you can use the buttons to go back/forward. But it doesnt work in nautilus and its driving me kinda crazy... 

I havent found any GUI in nautilus to change keybindings but since backspace works for going back i figure it must be possible to change it..?

Thanks for any help!

---

### Post by Eyeron on 2009-09-20
I have the same issue. am using a logitech mouse, is the brand a factor?
Also, if the buttons work with Firefox why aren't they working with the Epiphany browser?

---

### Post by FuturePusher on 2009-09-20
You can do what I did, this works great in all aspects I've come across with it (during probably a year's use!).

Make sure You have something like "xbindkeys" installed (it's in the repositories, so just "sudo apt-get install xbindkeys xbindkeys-config"!)...

What I did then was to "bind" mouse button 4/5 (whichever is the back button, just typing from memory here) to key combination "Alt+Left", and the other mouse button to "Alt+Right" (left/right keys are the arrow keys on keyboards).

You may have to look at the man-page for it, or find some of the existing guides/tutorials on the net, to find out how exactly to do these bindings (best done in it's config file, in You home-directory).


Here's an explanation of how it does it's job:

When You click the back button on Your mouse, "xbindkeys" notices and spits out emulated keyboard key presses, and those will wind up in whatever app You have in focus.

It "just so happens" that the key combinations "Alt+Left"/"Alt+Right" are "universally recognized" as "back/forward actions"... so it's been working great for me in both Nautilus, multi-tabbed Gedit/Gnome-terminal, as well as browsers (Seamonkey & Firefox... _without_ interfering with Firefox' builtin mousebutton sensing!).

I switched entirely from Wind0ws a bit more than a year ago, considered a power user/admin by most other computer users around me... and I've gotta say: whatever can be done in any other OS, can be done _better_ on a Linux system, just learn what to "tweak"!

And Ubuntu is the best since sliced bread! :guitar:

---

