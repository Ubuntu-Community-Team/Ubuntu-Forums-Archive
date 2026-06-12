---
title: "Dell Inspiron 6400...what now?"
date: 2007-06-07
forum: Dell  Ubuntu Support
---

### Post by smitty2point0 on 2007-06-07
Hello everyone! I hope this isn't in the wrong forum...cause I'm a TOTAL NEWB with unix. I had to google how to change directory's in the terminal for goodness sake. 

I have a Dell Inspiron 6400, intel core2 duo, 2 Gigs of Ram, ATI Radeon X1300 256mb.

I followed the instructions in the thread posted below ["Howto Install Feisty & Beryl On Dell Inspiron 6400, ATI x1400, Dell 1390 WiFi"]("http://www.ubuntugeek.com/howto-install-feisty-beryl-on-dell-inspiron-6400-ati-x1400-dell-1390-wifi.html")

Everything seems to be working great. I have Beryl running with skydome and everything. I can't enable 3D because it causes Beryl to crash I believe.

NOW TO MY QUESTIONS.....Is there something I should do to make the 3D work? I think it has something to do with the video driver that came with the instructions I followed.

Also, I have managed to get the Virtual Box running and I have installed XP PRO on it with, 10 gig partition, 512 Ram, 64 megs of video. 

The problem with that is....every time I restart laptop and try to open xp in Virtual Box, it tells me I don't have the rights to run it and have to run the sudo chmod 666 /dev/vboxdrv command....if I try it without the SUDO I get somethin saying I don't have rights to do that command?

What should I do? Again...I'm a total newb, so don't laugh me off the forum!!!

---

### Post by kill4killin on 2007-06-07
If you are running Beryl, frankly, be glad it works at all, that is still a beta product and as such is still going to be glitchy to some extent. I used to run it and it works pretty well but I found it to crash a bit more then my liking so I switched back to Metacity and Xorg rather then Emerald and XGL.

As for the permissions thing, I'm not sure how to help you there. I know a good bit but permissions on programs is not my specialty unfortunately. 

P.S. if you want to learn the linux commands and not do a whole lot of googling check out this link below, it's rather useful.

[http://www.computerhope.com/unix/overview.htm](http://www.computerhope.com/unix/overview.htm)

---

### Post by PriceChild on 2007-06-08
wrt to your 3d issue.

You are using something called "xgl" which basically steals all your 3d goodness so that you can run beryl/compiz. The only way you can get 3d acceleration back is by starting applications on a seperate X server, or disabling/removing XGL.

If I were you, I would search these forums for a "nonXgl" which will give you a guide so that you can run apps say "nonXgl glxgears" and have 3d acceleration.

---

### Post by smitty2point0 on 2007-06-08
Thanks for the info! That permission thing really is annoying, but I guess I can live with it!

Thanks again.

---

### Post by PriceChild on 2007-06-08
Yeah I have no clue about the virtualbox sorry... have you tried finding their support site as I'm sure you might be lucky and find it in their FAQs.

---

