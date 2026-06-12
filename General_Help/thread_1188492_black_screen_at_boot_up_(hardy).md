---
title: "black screen at boot up (hardy)"
date: 2009-06-15
forum: General Help
---

### Post by Megrimn on 2009-06-15
I realise that this is a recurring problem in the community, but I have a semi-unique situation here...

I've installed ubuntu on my dad's compaq 1200 laptop.  It was a pain in the neck, because the cd drive is shot.  Doesn't work. So I removed the HDD, put it in a different computer, and installed it there.  Trouble was, after it was back in the original computer, I got the black screen after GRUB. So after some searching, I put the HDD in the other computer, and was able to modify the monitor settings with the command "sudo displayconfig -gtk".

Well, my idiot brother tried to put windows back on it when I went off to college. Without success, I may add.  That was why I put Ubuntu on it in the first place.  

So I nabbed the laptop back, and since dad likes windows so much, I put kubuntu on it this time.  Unfortunately, I had to leave before I had finished, so I brought the computer with so I could get it running and bring it back later.  I don't have another computer I can pop the HDD into.  The only one I could use is the HP pavilion sitting downstairs, but the power pack is shot (I touched it after I plugged it in and it made me jump. Electricity is fun!)

So, I have to try to set kubuntu up for VESA while the HDD is in the computer that shows the black screen at boot.  Again, the cd drive is shot, so I can't use the live cd.  Is there some code or I can use in GRUB or something?

Thanks in advance.

note: already tried xfix in recovery mode.

---

### Post by Megrimn on 2009-06-15
Is there a way I can edit /etc/X11/xorg.conf from grub or recovery mode?

---

### Post by Megrimn on 2009-06-15
ok, I was able to edit xorg.conf in recovery mode as root with

```
root@laptop~$ nano /etc/X11/xorg.conf
```

which is great, save I still need to somehow get VESA running, and that isn't in that file, I guess.

[EDIT] k, got it working.  If you want to know how, just leave me a message.

---

