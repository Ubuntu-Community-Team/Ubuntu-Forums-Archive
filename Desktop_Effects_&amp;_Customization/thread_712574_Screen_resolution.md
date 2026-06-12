---
title: "Screen resolution"
date: 2008-03-01
forum: Desktop Effects &amp; Customization
---

### Post by himalakas on 2008-03-01
Dude, I changed the screen resolution and after reboot it gives an error telling "resolution out of range" (no display). Please help  me to fix this.

---

### Post by Locutus_of_Borg on 2008-03-01
dpkg-reconfigure  xserver-xorg

 should give you the option to change it to something within range, just lower it to what it had been, then find out what your maximum can be before changing it to that

---

### Post by himalakas on 2008-03-01
So how can I change it? I can only go to the kernel in recovery mod.

---

### Post by Locutus_of_Borg on 2008-03-01
thats what you type in while at the terminal in recovery mode

---

### Post by himalakas on 2008-03-01
On boot options menue it gives,

Linux mint, kernel 2.6.22-14-generic
Linux mint, kernel 2.6.22-14-generic (recovery mode)
Linux mint, kernel memtest86+

From this menue, I selected the first option. then it says in a black background -

    Attention
  Out of range
H:35.5KHz  V:174.0Hz

So, I can choose ony the second option which is [Linux mint, kernel 2.6.22-14-generic (recovery mode)].

So please help me to fix this in this mod.

---

### Post by Locutus_of_Borg on 2008-03-01
when you boot into recovery mode, you boot into a command line, at that command line type in ```
sudo dpkg-reconfigure xserver-xorg
```

choose a lesser resolution

---

### Post by himalakas on 2008-03-01
ThankYOU soooo much macho... I could fix it, Thankyou very very much for the help. So SEE YOU LATER. ("macho" means dude in our language- "Sinhala")

---

