---
title: "Help! Gnome theme overriden by KDE theme!"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Fyda on 2006-08-30
**UPDATE: I found what was causing this problem -- see post #2 for the new problem.**

Hi... I need help with a strange problem.

After I did [FONT="Courier New"]sudo aptitude install kubuntu-desktop[/FONT] and then rebooted, my GNOME session is graphically messed up. By "messed up," I specifically mean that the panels and apps (even the GNOME apps!) are being rendered *using the KDE theme, instead of the GNOME theme* (which was in use before and during the installation of Kubuntu).

So -- how do I fix it so that only the KDE session uses the KDE theme settings, while GNOME reverts to the GNOME theme settings? It looks horrendously ugly right now. (*That*, I know, is my fault for having an ugly theme in the KDE session -- but it looked good in that DE. Here it clashes with everything.)

Also, I am alarmed to find three of my panel applets crashing upon logging into the GNOME session. :( Strangely enough, the system icons have not been affected.

Here's some background info, which may help to pinpoint the causes and what I should edit:

Up until only a week ago, I had Ubuntu + kubuntu-desktop + xubuntu-desktop + E17 installed. This issue didn't exist back then; they were all self-contained (except for AmaroK being displayed in the KDE system colour theme while running under GNOME... which has always been the case anyway, and makes sense).

For some reason (I'm guessing a corrupted boot sector), Ubuntu then "died", as in, could not even be *attempted* to boot up. After powering up the machine, instead of GRUB loading and starting up Ubuntu, I got this very ominous message, by itself:
> PRESS A KEY TO REBOOT
I went into BIOS and set it to boot from the Windows XP hard drive*. The result was indefinite stalling at the point where WinXP was supposed to start loading. In a thorough panic, with both OSes suddenly totally unbootable (not even a shell to edit GRUB settings with!), I booted off the Kubuntu Live CD and did a reinstall.**

I don't understand why, but installing Kubuntu *then* doing [FONT="Courier New"]sudo aptitude install ubuntu-desktop[/FONT] is *not* the same as the reverse -- it resulted in the same graphical issue I'm having now (the KDE theme and widgets showing up in GNOME). When that got happened, I looked around for a solution, couldn't find one, and decided to just reinstall -- only this time, with the **Ubuntu** Live CD. The problem went away. And now, after installing [FONT="Courier New"]kubuntu-desktop[/FONT] (because I want to have both DEs), the problem is back. :(

I'm sorry for the length of this post, but I felt it necessary to explain more thoroughly, in the interests of aiding anyone who tries to help.

Thanks in advance,
Fyda


**Footnotes:**
* I have three physical HDs; one of them contains a dozen data partitions, the other is an 8GB one-partition installation of WinXP, and the third is a 13GB three-partition installation of Ubuntu.

** I don't know if he'll read this, but I really have to thank Aysiu for his guide on partitioning. If it weren't for that, I'd never have known to make a separate */home* partition, and would've have to wipe out my settings and personal files in the process of reinstalling. I was overjoyed to boot into the new installation of Ubuntu and find everything -- the theme, my Gaim logs, my Firefox bookmarks -- waiting for me. Thank you so much!

---

### Post by Fyda on 2006-08-30
Hmm. Okay, I remembered there was a setting in KDE for making GNOME applications look like KDE. I went and changed that (under *System Settings -> Appearance* -> *GTK Themes & Fonts*) to render all GNOME apps in the Human theme. It works! Now my new problem is this:

That settings dialog offers me a list of GTK themes to use. However, it does not include *all* of the themes I have installed -- in particular, I have a theme called *macosx-controls* installed, and it's not on that list. How can I refresh/update the list of themes recognised by KDE?

Thanks again,
Fyda

---

### Post by Fyda on 2006-08-30
Still no replies... and I've just found that features like the "mouse over to play preview of sound files" in Nautilus have *vanished* ever since this problem came up.

Can someone **please** tell me how to make KDE just completely leave the GNOME session alone? I'm getting very frustrated with this.

Thanks.

---

### Post by Fyda on 2006-09-08
SOLVED: After giving up on this issue and settling for Silicon (which was the only acceptable theme I could set in KControl for GTK apps), I stumbled across [this thread](http://ubuntuforums.org/showthread.php?t=134284&highlight=gtk+kde), followed the solution there, and now my Ubuntu is finally back to normal!

Here's the relevant solution from the other thread:


[quote=SlugO]I was poking around the ~/.gtkrc-2.0 for the first time actually and it looked like this:

---
# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Clearlooks-DeepSky/gtk-2.0/gtkrc"

style "user-font" {
font_name="Sans Serif 10"
}

widget_class "*"
style "user-font"
gtk-theme-name="Clearlooks-DeepSky"
gtk-font-name="Sans Serif 10"
---

When I remove or comment out the include part I can finally get all my GTK themes working perfectly. Except for some Clearlooks_Cairo themes which seem a bit broken without that include.[/quote]

---

