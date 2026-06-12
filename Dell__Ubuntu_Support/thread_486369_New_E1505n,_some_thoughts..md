---
title: "New E1505n, some thoughts."
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by mike.123850 on 2007-06-27
Just thought I'd drop in and tell you what I think of my new Dell E1505n that came with Ubuntu. In a word .... great.  I'm a basic user ... e-mail, surfing, ripping MP3's, a little burning. No gaming or graphic arts stuff.

I had been using Xandros since version 1 up through version 4. Though, like many of you, I have used many other distro's as well.  I am thrilled that Dell has decided to sell machines with a Linux distro on them. Being Ubuntu made my decision to buy one a no-brainer as I had used it's live cd version and was happy with it. I also wanted to vote with my wallet because that's what the corporate types understand.

Anyhow, all the necessary codecs are installed and so is Java 6, I'm using the nvidia-glx installed from the restricted drivers. Everything is running wireless on a Buffalo WHR-HP-G54 access point/router. By the way, I'm just using the updated stock Buffalo firmware and not Tomato or DD-WRT. Frankly, I have not seen it necessary to do so ... yet. :)

Also, I am using a Linksys PSUS4 print server on my HP 960c Deskjet. Couple of items here which may be of interest. The default password for the Linksys PSUS4 is "admin" without the quotes which isn't mentioned in the manual. I hard set it's IP address. I then set my machine as a Unix Printer (LPD), set it to the IP address that I hard set on the PSUS4, set the queue to L1. This all works great.

My wife's old IBM ThnkPad is also set up wireless using a  LINKSYS WPC54G-WB card. All the machines can see each other, and use the printer. All in all, everything seems to be working very well.

I have enjoyed reading through the many useful posts on this forum.  It made everything I needed to do pretty darn easy.

mike

---

### Post by kill4killin on 2007-07-06
I'm glad to hear that you are enjoying your 1505n. I bought that same laptop before they started offering it pre-loaded with Ubuntu and I dealt with Windows XP for about a month and decided that I had to install Ubuntu on here after using it for about a year on my desktop and many other distros before that. The only hitch that I had with my laptop is that since I bought it before they started to preload them with Ubuntu, they were still offering it with an ATI card so I went and got the ATI x1400 graphics card, which, if you have been following the bugs at all, has a major bug at the install that requires you to use the alternate install cd and then install the graphics drivers in consol before ever allowing you to get into a graphical interface. Other than that I got the Intel Pro-wireless 3945 card and it worked right out of the box with absolutely no configuration besides finding out where to get network-manager .0.6.5 so I could do the newer security protcols.

---

### Post by gdmix on 2007-12-24
Thanks Mike. After messing around with my print server for a while, &#8220;L1&#8221; for the queue was the only part I was missing.

Edit: I have a E1505 also, that came with Vista. I'm about to shrink the NTFS partition even further, leaving just enough for the OS, and the few Windows only apps I use.

Everything works well for far. I have it set to use my Dell 2407WFP monitor when it's plugged in and default to the laptop screen when it's not (using nvidia-settings.) The only thing it wont do that the driver under Windows will, is dual-view with different resolutions.

---

### Post by cartisdm on 2007-12-25
I duel boot my e1505.  Wish I hadn't paid for XP though as I almost never use it.  When you purchased it with Ubuntu did they already have most of the plugins installed or did you have to configure that stuff when you got it?

---

### Post by fjgaude on 2007-12-26
My E1505n works fine... I installed everything using Automatix when I was using the 32-bit Feisty as installed by Dell.

Now, I've blown out everything Dell had in there, the three partitions, and installed Gutsy 64-bit on one big partition. The only issue I have is Suspend doesn't come out of its sleep. All else, WIFi, etc., work fine. I do believe the 64-bit is a little faster. Notice my signature.

Thanks to all who have made this possible. Ubuntu rules!

---

