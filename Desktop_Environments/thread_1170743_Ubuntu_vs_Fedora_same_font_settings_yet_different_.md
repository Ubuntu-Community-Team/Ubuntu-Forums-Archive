---
title: "Ubuntu vs Fedora: same font settings yet different look"
date: 2009-05-26
forum: Desktop Environments
---

### Post by notfound123 on 2009-05-26
I have two systems running side by side: Ubuntu 9.04 and Fedora 10. Both with GNOME, both out of the box with no customizations, same monitor, same video card.

I have set both to 96dpi resolution, size 10 font, and made sure all the other font settings were the same. Yet, for some unknown reason, Fedora's GUI fonts look so much smaller (which is what I want). 

How come Ubuntu's settings don't match? I have tried changing the font size down to 8 or 9, but still can't match it. What gives?

---

### Post by notfound123 on 2009-05-27
Anyone? This isn't because of the Gnome version difference (2.24 vs 2.26), is it?

---

### Post by fballem on 2009-05-27
Another suggested cause: I think ubuntu will allow for the easy installation of proprietary drivers - in my case the nvidia drivers. In fedora, it is more difficult to install proprietary drivers - they will typically use open source drivers. This might account for the differences - the video _cards_ may be identical, but the _drivers_ may be different.

---

### Post by coffeecat on 2009-05-27
Have a look in /etc/fonts/conf.d in Ubuntu and see which font rendering configuration files are linked from /etc/fonts/conf.avail. Now do the same in Fedora. You'll see that they're different, sometimes even with different code in the same-named files. Font rendering is a complicated business - it's way beyond me - and it seems that each distro approaches it a little differently. Try OpenSUSE 11.1 - different again.

But, as fballem said, this also might be down to a different video driver, or even a different version of the xserver. What video card are you using, and what drivers are you using in Ubuntu and Fedora?

---

### Post by notfound123 on 2009-05-27
> **fballem said:**
> the video _cards_ may be identical, but the _drivers_ may be different.

Great point!!! I bet that's what it is. I did install Nvidia's drivers on Ubuntu; didn't do so on Fedora.

---

### Post by notfound123 on 2009-05-27
Ok, here is the latest. To be fair in my comparison, I compared both distros side by side running in VMware. The fonts do look identical to the ones I get on stand-alone desktops (so the video driver cant be the cause).

See attached.

Notice how Ubuntu's window and the fonts are much wider then Fedora's/XP's...

---

### Post by floborg on 2009-05-27
Since it was Red Hat that created the Liberation fonts, there is a good chance that Fedora has mapped "Sans" to Liberations Sans.  Ubuntu maps it to DejaVu Sans, which I prefer on my CRT monitor using the "best shapes" option.  The screenshot, to me, looks like they've used Liberation.

You can test the mapping by opening up the font chooser and switching between Sans & Liberation Sans, and Sans & DejaVu Sans.  Do that while looking at the preview text.

---

