---
title: "Grub resolution"
date: 2006-04-28
forum: Desktop Environments
---

### Post by corvax on 2006-04-28
Does anyone know of a way to make grub use more than 14 colors for its background /splashscreens I know lilo can use 256 colors anyway to make grub use 256? Or more? 
Any help or ideas is appreciated thanks..

---

### Post by jazzmuzik on 2006-04-28
have you tried adding "vga=###" to menu.lst where ### is a video mode? Search this forum for vga= and see what success others are having. The ### number will be different depending on your video card's capabilities.

---

### Post by mjm115 on 2006-04-28
Grub only supports 16 colors.

[https://wiki.ubuntu.com/GrubHowto#head-860336ddfd132cb25712427a8c583398cee6fd96](https://wiki.ubuntu.com/GrubHowto#head-860336ddfd132cb25712427a8c583398cee6fd96)

Also, [here]("http://ruslug.rutgers.edu/~mcgrof/grub-images/#1.0") is a good tutorial for splashimages for GRUB (take a look at the requirements).  Once you've loaded your OS, you can change the the colors and resolution, like jazzmuzik was saying, but as far as the GRUB menu, you are limited.

---

### Post by judofyr on 2006-04-28
What's the point? The menu os just shown for about 10 seconds...

---

### Post by Herman on 2006-04-28
I was following the same tutorial just yesterday and made some grub splashes with it, I enjoyed it and I think they do make a difference. Mine are only 14 colors.
It's true they only show normally for 10 seconds unless I pause it to show someone how dual booting works. I think it does make a difference to have the grubsplash looking nice.
The ones I made have the official Ubuntu and Kubuntu logos and colors. The hardest part was getting the edges of my lighter-coloured rectangle in the middle lined up with my grub menu's center area border.

---

