---
title: "One got to love a Live CD/DVD !! Fixing a borked grub menu.lst"
date: 2008-12-11
forum: General Help
---

### Post by Reiger on 2008-12-11
Recently (after finally getting my wireless up & running) did an 
```

sudo aptitude update && sudo aptitude upgrade

```

Which nicely updated my system but reported that I had a custom grub menu.lst and whether I wanted to keep that instead of the new one? I choosed to keep my old one. So far so good right?

I was a little worried though, so I looked what my grub menu.list actually contained after updating... Suffice to say I was not very pleased to see there was *not a single* boot option left. 

But not to worry, I thought: just try
```

sudo update-grub

```
For sure I had seen the aptitude program executing that command, seen it find a bunch of entries ...

But to no avail.
So I searched for "grub" in the repositories and installed kgrubeditor as well as grub2:
```

sudo aptitude install kgrubeditor
sudo aptitude install grub2

```

Grub2 cleanly retrieved my Vista booting options as well as numerous Debian/GNU Linux options (odd, but the kernel versions matched my set up so I though that'd be ok). After restarting my system all my boot options except for the Vista ones will die leaving a cryptic "device string not recognised" message.

So what do I have so far:
(a) I can boot into grub.
(b) I can use grub to load Vista.
(c) But I can't chainload into grub2 (for same reason as under d)
(d) And all my other options (Linux 2.6.27-9/ 2.6.27-7 both generic & recovery as well as a memtest86 one) will fail at the "unrecognised device string" message.

But who is defeated so easily? I still have this live CD/DVD around and well, mounting the internal partition which contained my now-nearly-defunct root partition (which happens to include my /boot/ directory), using a copy the grub menu.list from my laptop as sample I found out that:

(a) I could actually *edit* the file using
```

gksudo gedit /path/to/menu.lst

```
... More power to those who use Live CD's/DVD's apparently... 
(b) The grub2 install had made a mess of the 'root' parameters in the menu.list. It had copied the content of a certain similar parameter over what should have been a hard drive partition address. ("root==UID=.*" instead of something comprehensible like (hd0,1) or (hd0,6))
(c) Replacing these UID strings with harddrive addresses fixed it (as expected). Naturally, I had miscalculated the addresses so when I tried it still would not work (Error 17: Failed to mount partition) but some command line guess gave me prove of concept that it would've worked (I had used (hd0,6) where it should've been (hd0,5)).

So apart from being more than a little pleased at fixing this myself without re-installing anything...

I've got a few questions left:
Is this (the mistaken root values) a 'known' grub2 bug?
Any idea what might've caused update-grub (the sudo aptitude update && sudo aptitude upgrade story) to go barking mad and remove all my boot entries in the original menu.lst file? Could be handy to know next time I edit the file.

---

