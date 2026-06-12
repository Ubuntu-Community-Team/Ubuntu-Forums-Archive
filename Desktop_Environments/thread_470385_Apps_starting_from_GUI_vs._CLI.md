---
title: "Apps starting from GUI vs. CLI"
date: 2007-06-10
forum: Desktop Environments
---

### Post by tcv on 2007-06-10
Hey folks,

I have a problem I hope someone can help shed some light on. I am running Ubuntu Feisty.

Earlier this week, I successfully installed gnome-mplayer and the gecko-mediaplyer plug-in for Firefox. When I first tried it, I had some instability problems and during the course of troubleshooting I was able to narrow it down to a reproducible event.

Here's how it lays out:

On the following page ([http://www.apple.com/trailers/newline/rushhour3/](http://www.apple.com/trailers/newline/rushhour3/)), gecko-mediaplayer and, subsequently, gnome-mplayer are invoked three times.

If I run firefox from the command-line under my own user account (not sudo or su), then I can successfully access this page and launch any of the trailers on the page.

If I run firefox from Gnome by the icons, Firefox-bin jumps to 75% CPU and higher and never completes the page. I can see that gnome-mplayer is invoked three times by checking out the process list, but Firefox hangs.

So, my first question is: Can there be something different between how firefox loads from the CLI versus double-clicking an icon in Gnome?

And any other thoughts are greatly appreciated.

Cheers,

Mike...

---

