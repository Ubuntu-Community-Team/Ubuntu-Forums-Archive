---
title: "Cairo-Dock Transperancy Issues In Jaunty"
date: 2009-04-25
forum: General Help
---

### Post by zhork on 2009-04-25
I made a fresh install of Jaunty. I installed cairo-dock. 
This time, unlike on my previous install, it had issues with transparency around the borders. See the lines between icons in image?
I cant figure out whats wrong, any help on removing the lines would be much appreciated.

[IMG]http://xs538.xs.to/xs538/09176/screenshot243.png[/IMG]

---

### Post by fabounet on 2009-04-27
which version ?
which drivers ?
which options at startup ? (-o / -c ?)

---

### Post by zhork on 2009-04-28
I tried several versions, including the release candidate for version 2.

option -c produces what the image shows. option -o does not make the white lines, but transparency does not work (there is a black box behind the bar)

My (crappy) card is a Radeon 7200. AFAIK the card is not working, the driver comes with ubuntu and i enabled it in the xorg config.

The "hardware drivers" under system > administration is empty. When i had the previous ubuntu release it was full of drivers, which automatically had shown up there.

this leads me to conclude i had something installed that let opengl work for my card before...

---

