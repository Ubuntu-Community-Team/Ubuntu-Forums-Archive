---
title: "monitor troubles"
date: 2006-01-05
forum: Desktop Environments
---

### Post by Hairy_Palms on 2006-01-05
For christmas i got a new TV/Monitor to replace my ageing CRT however it has a low refresh rate, windows is fine with this, but ubuntu isnt, 
ive tried reconfiguring the xserver, but no matter how many what if i pick a resolution and refresh rate above 800x600@56hz i get an out of range from my monitor, in windows i run it at 1280x768@60hz so i cant understand what the problem is. 
Same trouble in Suse10 as well, its a wharfdale LCDTV plugs into standard VGA port and my gfx card is a Vanilla Geforce3 with the nvida drivers installed and it all worked fine on my old crt :(

---

### Post by 23meg on 2006-01-05
Did you try the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=83973")?

---

### Post by Hairy_Palms on 2006-01-06
thanks for that, i can get a picture now, turns out my monitor doesnt do 60hz, it does 59hz, but for some reason, i still cant get widescreen resolutions even when i manually add the lines to xorg.conf any ideas on how to get 1280x768 as a resolution? 
xorg automatically added the entry saying it but i cant use it,

---

### Post by Hairy_Palms on 2006-01-26
i made my monitor work at 1024x768 in Suse 10
ubuntu refuses to run at anything other than 800x600 i really want a widescreen resolution. please someone help, the modeline generators didnt do anything.

---

### Post by hashimoto on 2006-01-26
Did you run:
```
sudo dpkg-reconfigure xserver-xorg
```
You need the details of your monitor to get everything right and I've found this to be the best way to configure.

---

### Post by Hairy_Palms on 2006-01-26
yes i ran it lots of times, thats what i did in the first post. i have to manually put in the refresh rates just to make it display anything, but it doesnt let me use 1280x768 or 1024x768 even if i select them in dpkg-reconfigure

---

