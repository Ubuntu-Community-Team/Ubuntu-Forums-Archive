---
title: "nVidia boot/virtual terminal corruption"
date: 2011-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jsbiff on 2011-01-23
I've been having a problem since upgrading from an earlier version (I think 8.04?) of Ubuntu to 10.04 (I didn't directly upgrade - I used the Update Manager to first upgrade to 9.04, then again with the Update Manager to upgrade to 10.04. I'm running the AMD 64-bit generic kernel, and have an nVidia 8700M video card in my Dell XPS M1730 laptop.

Since upgrading, my 'text consoles' are graphically corrupted, and I can't seem to figure out how to fix them. What I mean is, when the computer is booting up (which might actually supposed to be showing a low-res graphical mode, I think, but X.org hasn't yet loaded - it's just the kernel graphics driver), or if I use ctrl+alt+F1 (or F2, etc) to switch to one of the text virtual terminals after X has loaded, the screen is all corrupted.

X.org works fine, and all applications which run under X, but I'm worried that if ever I have a problem with X, I won't even be able to go in and fix it with the text virtual terminal (well, I can boot from Grub into recovery mode, so I can *probably* use that to get a text console login for emergency admin).

Here's a screenshot (well, taken with the camera on my phone since I don't think I can take a screenshot of the screen before Gnome is running, or when I've switched to a virtual terminal) demonstrating what it looks like (basically, the screen seems to be 'doubled' left-to-right - that is, the left half of the screen and the right half appear to probably be duplications of the same image),  and what's there is basically unreadable:

[img]http://farm6.static.flickr.com/5290/5382684140_7efa213907_z.jpg[/img]

I should probably also mention that I installed the 'startup-manager' gnome tool for making it simple to manage the Grub boot menu. It currently is set to boot with an 800x600x8 graphical mode. If any additional info about how the settings are set is needed, let me know.

I would be willing to post the grub config files, if that would be helpful.

---

### Post by mikewhatever on 2011-01-23
That is probably the cause - 800x600x8. Can you change it to something higher, like 800x600x24?

---

### Post by rodrigo6k on 2012-08-30
Hi, i'm quite newbie in terms of linux.
I know this post is a bit old, but i have the same problem with my laptop. 
Graphics are corrupted and the terminal is unreadable.
Did you manage to repair it?

Thanks in advance

---

