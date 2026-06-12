---
title: "on fonts, font management and the maximum number of fonts gnome can handle..."
date: 2005-12-11
forum: Desktop Environments
---

### Post by Makrie on 2005-12-11
HI.

I have a large number of fonts (20,000+), which on my windows system I managed through Corel's Bitstream font manager.

Last night I tried to put a folder containing all these fonts into /usr/share/fonts - it meant I couldn't log into gnome... it hung at the brown rectangular start screen. I was able (after advice) to log in to a command line and delete the fonts folder I had added and it then rebooted fine.

So, some questions...

Would it be okay if I just left it longer (say an hour?) at boot with all fonts installed? It's not like I have to reboot often so that could be okay, if the system would function well with all fonts installed afterwards...

If that's too many fonts, how many is a reasonable number to have installed? Windows 2000 always said 400 but would be fine up to 1000 or so (IIRC).

What should I use to manage the remainder? I've heard of DEFORMA, and it's installed, but I don't know wher to find it... is there anything else I should be looking at?

Would I be better off putting all the fonts in my user directory rather than the system wide fonts directory? Really, whatever works best!

Any advice on running Ubuntu with a great many fonts gratefully received.

My system (FWIW) is a Dell Poweredge 700 P4 2.8 with 1.5Gb of RAM and mirrored SCSI drives running Breezy.

Thanks

Makrie

---

### Post by khc on 2005-12-11
Are these all True Type fonts? If so, you can use the command fc-cache to force fontconfig to regenerate the font caches, that will probably speed up next log in. man fc-cache for more details.
As for managing fonts, I've never used a font manager, but nautilus gives you a preview of the font if you open a directory containing fonts. Deforma has nothing to do with that.

---

### Post by dangermouse28 on 2006-07-11
Ok - I realise that it's been a while since this was raised, but I think I have a suggestion. I've got 8000+ fonts and when you load these all into .fonts, it causes no end of grief. It's also far too many to be usable (you really want to scroll through 8000 fonts looking for the right one?). What I did was this.

Because there's no mature font manager package available, use Nautilus to preview fonts. But because it takes forever to render thumbnails of thousands of fonts, divide your font collection into folders a - z. I also have 3 folders: Graphical Fonts, Fun Text, Standard Text which I use to categorise fonts I've already used (so I know where to find them again). I also have a folder called Windows Fonts which contains fonts distributed with MS products.

At any time I will have a copy of the Windows Fonts folder in .fonts and then load in (or remove as required) other font folders. What I didn't know was that fonts can be grouped in folders under .fonts and are still available to Gnome. This makes font management a doddle - just remember to copy, not move or else you'll lose something when periodically clearing out the .fonts folder!

---

### Post by Makrie on 2006-07-11
Thanks for that! It seems a good 'working' solution. I'll play around with it later today... I didn't know .fonts could handle folders - o me of little faith!

In my searching I also (why haven't I set this up yet!) found a lovely looking program called fontlinge ([http://www.gesindel.de/](http://www.gesindel.de/)) which creates a database of your fonts which you can view through Apache and use to print out sample pages... mmm, A3 sample pages of all my fonts!

Right. Thanks to your post I'm suitably inspired to play with the .font folder and to try more to install Fontlinge - I seem to remember it went dreadfully last time, it has to go better this time, right? fingers crossed!

If anybody does get Fontlinge working, I'd love to hear!

---

### Post by revertex on 2006-07-25
defoma is the answer to your question.
take a look at defoma manpage.
whith defoma you can provide some set of fonts to specific applications without hog your system.

---

