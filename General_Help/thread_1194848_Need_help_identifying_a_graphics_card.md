---
title: "Need help identifying a graphics card"
date: 2009-06-23
forum: General Help
---

### Post by vajarrm on 2009-06-23
I have recently been given an old PC that has a graphics card like I have never seen before. Its absolutely HUGE, far longer than any card I have ever seen, and it requires an external power adaptor for the card itself. 
I have tried booting several Linux live Cds to run lspci, but they all freeze when they go too boot into X.

Does anyone have a clue what card this is and how I can get it Ubuntu too boot on it?

---

### Post by sim-value on 2009-06-23
Does this PC have an  Onboard GPU too ?

---

### Post by vajarrm on 2009-06-23
> **sim-value said:**
> Does this PC have an  Onboard GPU too ?

No unfortunately, its a pretty old machine.

---

### Post by sim-value on 2009-06-23
Try the gentoo live CD maybe ... its CLI only ...

---

### Post by vajarrm on 2009-06-23
Ok, lspci identifies it as;
[FONT=monospace]
[/FONT]VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 5 / Voodoo 6000 (rev 03)

Now I know what the card is, does anyone have any idea how I can boot X on it?

Thanks.

---

### Post by snek on 2009-06-23
Wow a Voodoo 5, that's a pretty cool and exclusive card.. Hold on to that baby, as far as I remember the 5 and 6 are basically worth money because they were the last series 3DFx released before it was bought by nVidia.

In terms of performance it is about comparable to the nVidia TNT2, if I remember correctly. It's from about 1997.

Some posts mention installing libglide3, you might want to have a look at that.

---

### Post by sim-value on 2009-06-23
Also going to the Help section might be an idea ...

/end of my knowledge

---

### Post by prshah on 2009-06-23
> **vajarrm said:**
> 
[/FONT]VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 5 / Voodoo 6000 (rev 03)
```
sudo apt-get install xserver-xorg-driver-tdfx
``` Should install the correct driver, but _may_ not enable it; to enable it you need to add the relevant lines to your xorg.conf. Posting your xorg.conf will help, but you can try this anyhow; From the terminal (Applications-Accessories-Terminal)```
sudo pico /etc/X11/xorg.conf
```

Locate the section titled 'Section  "Device"' - Should be the first one. Delete any lines titled "Driver" within the section. Add the line```
Driver   "tdfx"
``` anywhere within the section. Save and exit (Ctrl+X, y, enter)

From the prompt, attempt to start X```
startx
``` If it fails, post back your /var/log/Xorg.0.log file for more clues.

---

### Post by caravel on 2009-06-23
Those cards work very well under Linux.  I used to have one of those back in the day... brings back memories.

---

### Post by lovinglinux on 2009-06-23
[http://en.wikipedia.org/wiki/Voodoo_5](http://en.wikipedia.org/wiki/Voodoo_5)

---

### Post by spoons on 2009-06-23
The Voodoo 5 6000 was never actually released to the public. They're very rare and wroth quite a lot.

---

### Post by lovinglinux on 2009-06-23
> **spoons said:**
> The Voodoo 5 6000 was never actually released to the public. They're very rare and wroth quite a lot.

Sell it on ebay, I think you can get more than [$1,000.00](http://www.neoseeker.com/forums/406/t29467-voodoo-5-6000/) for it, maybe more :)

---

### Post by CharmyBee on 2009-06-23
> **snek said:**
> In terms of performance it is about comparable to the nVidia TNT2, if I remember correctly. It's from about 1997.

It's more of a contender versus the Geforce2 MX AGP. It's released in 2000. They didn't come out with the Voodoo2 in 1997 yet.

Anyway the Voodoo5 6000 is a **very rare and unstable card**, you're best off by _not using it_ and getting rich off some 3dfx fanboy who would pay their liver for it. There are plenty of fans who would love to have what you have, even though it's just an infamous, obsolete piece of history.

---

