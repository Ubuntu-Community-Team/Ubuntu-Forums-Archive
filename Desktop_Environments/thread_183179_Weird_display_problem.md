---
title: "Weird display problem"
date: 2006-05-27
forum: Desktop Environments
---

### Post by zoomcookie on 2006-05-27
Hi Everyone,

This is my first tine here so forgive me if this post is in the wrong forum. I have very recently taken the plunge and set my Toshiba SM30 laptop to dual boot Ubuntu and XP. Ubuntu seemed fine at first but following an online update most items on my screen are now fuzzy. This is not just the fonts, it is the windows, icons, everything. Fuzzy may not be a very good description. In a few places it seems ok. A better description would be that rather than screen elements being drawn with solid lines everything seems to be made up of closely spaced dots. You can clearly see the gaps between the dots. Does that make sense?

My laptop has a widescreen display and defaults to 1280x800 normally. Ubuntu worked at this resolution perfectly before the update. All resolutions below 1280x800 seem ok, I am guessing it's a driver issue or something. 

My graphics chipset is an nVidia G-Force FX 32mb.

Can anyone shed any light on this?

Many thanks

---

### Post by Sukarn on 2006-05-30
Did the update include a kernel update?

---

### Post by impakt on 2006-05-30
same thing happened to me on a machine i rarely use but works fine on my normal box. Interested to see what the reason is. :confused:

---

### Post by zoomcookie on 2006-05-30
Thanks for the replies. I actually cant remember if the update included the kernel or not. How can I look back to check?

---

### Post by Sukarn on 2006-05-31
At boot time do you get a new kernel option to boot (in GRUB)?

Try this -
```

1) Press Ctrl + Alt + F1 to get to command line only. It should not be fuzzy.
2) Log in as yourself.
3) type "sudo nano /etc/X11/xorg.conf" (*without* quotation marks)
4) give your password
5) find the section "Device" (*with* quotation marks)
6) replace "nvidia" with "vesa" (*with* quotation marks)
7) restart your computer (sudo reboot)

```

8) Tell us whether it worked or not.

---

### Post by zoomcookie on 2006-06-04
Hi, sorry for the slow response. I have been on holiday. I have tried as you suggested Sukarn but unfortunately it didn't help. I replace the Nvidia line with vesa but when I rebooted I ended up at a text screen saying could not start X or something like that. I am not at my laptop now so cannot confirm the message. Since then I have downloaded Fedora Core 5 and tried that but exactly the same thing happens. I selected vesa from within Gnome but then I can only get up to 1024 x 768. Not the resolution of my display. I am sorry I can't be clearer about what messages were displayed but I did not understand what it was telling me and I didn't make a note of it. 

I am willing to go back to Ubuntu if this can be resolved. If I can't get to 1280x800 I will probably just run XP. :-(

Thanks

---

