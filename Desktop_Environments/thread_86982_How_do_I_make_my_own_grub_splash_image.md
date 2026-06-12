---
title: "How do I make my own grub splash image?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by Sunnz on 2005-11-06
I created a 640x480 xpm file in gimp then gz it... but it does not seem to work... anyone here who know how to make grub splash image could give me some pointers?

Thanks you.

---

### Post by aysiu on 2005-11-07
I followed these instructions, and I was fine:
[http://www.tldp.org/LDP/LG/current/jayanth.html](http://www.tldp.org/LDP/LG/current/jayanth.html)

What does your /boot/grub/menu.lst look like?

---

### Post by Haegin on 2005-11-13
Ok, I managed mine eventually but I'm posting here in the hope that others may benefit from what I had to google for (its a hard life). The requirements for the splashscreen are that it has 14 colours and that it is in xpm format. The gimp can "convert" any normal image into this format.

1. Open the file in the gimp (I used v2.2)
2. Image > Resize - set it to 640 by 480 and click OK
3. Image > Mode > Indexed
4. Set the max number of colours to 14 (use generate optimised palette) [fiddle with the dithering if you want]
5. Hit ok and save using .xpm as the extension.
6. Add it to your /boot/grub/menu.lst file (there are other posts covering this so I wont repeat it all)

Hope this helps

---

