---
title: "Upgrading motherboard"
date: 2007-04-19
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-04-19
Ok Im thinking of dumping my crap Asrock motherboard, so I can have a wider choice (ie one that works!) of video cards. If I just swap over a different motherboard, will Dapper still boot ok? I understand things like sensors may be different, but as long as I can boot up, I can sort those. It currently a 3.06 Ghz Celeron 512Mb DDR333 memory 200GB HD. Onboard Intel graphics. When I saw how fast the graphics were on my 1.1Ghz Duron with a MX400 Nvidia running Edgy, I decided to get a better card on my main machine. Cant get any video card to get past "loading hardware drivers" on this crap ASrock 775i65GV.

---

### Post by dcstar on 2007-04-22
> **mister_p_1998 said:**
> Ok Im thinking of dumping my crap Asrock motherboard, so I can have a wider choice (ie one that works!) of video cards. If I just swap over a different motherboard, will Dapper still boot ok? I understand things like sensors may be different, but as long as I can boot up, I can sort those. It currently a 3.06 Ghz Celeron 512Mb DDR333 memory 200GB HD. Onboard Intel graphics. When I saw how fast the graphics were on my 1.1Ghz Duron with a MX400 Nvidia running Edgy, I decided to get a better card on my main machine. Cant get any video card to get past "loading hardware drivers" on this crap ASrock 775i65GV.

Change your xorg.conf file to use the generic VESA driver.

---

### Post by mister_p_1998 on 2007-04-29
And I would boot into a command line how?.....

---

### Post by craigsharp on 2007-04-29
When GRUB loads, you should be able to change some options,  read the bottom of the screen and there should be a command you can type to change settings.   Not sure what it is, i'll check and see then i'll get back to ya.

---

### Post by craigsharp on 2007-04-29
Yea,  when your GRUB bootloader comes up and asks what you want to load, instead of selecting the top most,  choose the second option.  It should boot into a terminal,  then you can edit your xorg file with your choice of editor.  I prefer pico because it's easy and straight forward.

Hope that helps man.

---

### Post by mister_p_1998 on 2007-05-01
Thanks,
Ill try that, what do I type exactly to select the VESA driver?

---

### Post by mozetti on 2007-05-01
```
dpkg-reconfigure xserver-xorg
```

That will get you to a somewhat graphical, automated xorg.conf editor. It asks what driver to use, and select "vesa"

or you can ```
nano xorg.conf
```

And change the driver to "vesa"

I forget the exact directory for the xorg.conf file, but either cd into that directory and use the code above, or just prefix "xorg.conf" with the directory path.

---

