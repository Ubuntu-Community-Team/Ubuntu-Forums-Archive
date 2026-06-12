---
title: "Thmes missing after Nvidia-driver install"
date: 2011-02-13
forum: Desktop Environments
---

### Post by JohnFante on 2011-02-13
I have just reinstalled 10.10. I used the alternate version since I had to add a fake raid Windows install. Ubuntu is on a OCZ SSD (very nice :-))

Install went fine. Update went fine (a bit over 300MB of updates) and everything looked as it should.

Then I installed the restricted Nvidia drivers for my GTX275 card and then gnome suddenly looks like the attached screenshot. I have tried to change theme and the colour of the top bar changes but that is that. No icon changes etc.

I have updated to the latest 270.18 drivers but the problem is still the same.

Any ideas on what to do?

---

### Post by Krytarik on 2011-02-13
See this ongoing megathread:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

---

### Post by JohnFante on 2011-02-14
Thank you for the link :-)

Found a solution.

---

### Post by Krytarik on 2011-02-14
> **JohnFante said:**
> Thank you for the link :-)

Found a solution.
What was it?

---

### Post by JohnFante on 2011-02-15
I did a sudo gconf-editor. Went into apps>nautilus>preferences, and scrolled all the way down. The next to last item should say theme. I edited the item, and remove the word default.

At first it did not do any thing so I was about to do the a restart script they listed also but after a few reboots everything looked as it should.

---

