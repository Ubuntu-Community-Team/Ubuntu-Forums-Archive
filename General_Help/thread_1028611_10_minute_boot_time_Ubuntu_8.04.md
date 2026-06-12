---
title: "10 minute boot time Ubuntu 8.04?"
date: 2009-01-02
forum: General Help
---

### Post by NoTownKasper on 2009-01-02
Ok, here's an odd one for you gurus and intelligent users everywhere. A couple of days ago, I swapped out my old login screen for a newer, shinier one from the nice folks at gnome-look. Nothing major...right? Well, after a reboot...my ubuntu system decided to freeze up cold right at the point where the screen blanks from the bootscreen, to show the login screen. The cursor shows, complete with the 'busy' animation (Think 'hourglass' in windows...but fancier, cuz this is linux :D ), and it just sits there.

So, instead of panicking and reaching for the install CD once more, I just let it sit there while I went to the restroom, got a soda...and when I come back...it's booted. After testing, Ubuntu runs -fine-. Nice and slick and fast like I've come to expect...but the boot time is suddenly around 10 minutes. I do a lot of boot swapping between Ubuntu and my win install...so this really isn't acceptable. Any ideas?

---

### Post by cmnorton on 2009-01-03
This sounds like X is failing and restarting, but its retries should time out well before ten minutes. You could boot into recovery, run dpkg-reconfigure xserver-xorg, and choose different settings for X; change video drivers. I run vesa on a Thinkpad T61p so it can run standalone and in a KVM environment.

You could also try changing monitor settings.

Look in the logs and the output of dmesg.

---

### Post by jerome1232 on 2009-01-03
And have  you tried changing your new shiny g/kdm theme for the one you were using before, I've had the occasional gdm theme cause me problems.

---

