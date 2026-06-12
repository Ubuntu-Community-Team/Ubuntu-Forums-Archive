---
title: "I screw the &quot;Subpixel smoothing&quot; installing the MS trutype fonts!"
date: 2007-12-23
forum: Desktop Effects &amp; Customization
---

### Post by v1ncent on 2007-12-23
I try the Mac4Lin (v0.4) to make my Linux look more like OS X, and i was installing all the 'fonts thing', but everything went wrong and the "Subpixel smoothing" (That comes out of the box in Ubuntu) doesn't work anymore!!

This were the instructions:
> Either download the fonts into your home directory and install them on your system:
"sudo tar xvjpf msfonts.tbz -C /usr/share/fonts/truetype/"
Or, enable non-free, universe and multiverse repositories and install the Microsoft fonts:
"sudo apt-get install msttcorefonts"
You now have the Microsoft fonts installed. Let's configure your system now.
Download the xml files and extract the file into /etc/fonts/ as root:
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
Log out from Ubuntu and relog in. Here's how your desktop will look like the attached screenshot.jpg file.

Of course!! in the end says:
> It's a lot more complex than disabling antialiasing at small font sizes
Take a backup of /etc/fonts folder and whatever you modify here first, in case you may want to revert.

I know, i was very stupid, but now i don't know what to do...
i need just to replace the /etc/fonts folder to the default one?
If that is the case, then, could someone give me the default /etc/fonts folder? Please! (or how to install it again, in the exact same way it was before)

THANK YOU!

---

### Post by Islington on 2007-12-23
could be wrong but couln't you just grab the default folder from your live cd?

---

### Post by tomauty on 2007-12-23
> **Islington said:**
> could be wrong but couln't you just grab the default folder from your live cd?

Yes that's what you'll have to do. I did the same thing, then figured out that was actually the script to install Sharp Fonts.

---

