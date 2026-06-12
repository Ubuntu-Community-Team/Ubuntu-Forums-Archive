---
title: "Custom Ubuntu DVD Install? Need for Company!"
date: 2009-02-28
forum: General Help
---

### Post by cinmachina on 2009-02-28
Hi all,

I'm working on a presentation at work to explain why we can replace many users PC's with laptops/desktops running completely free open-source software.

So far, I've been able to identify key apps that will be critical to our business functionality. OpenOffice, kvpnc, samba, Lotus Notes 8.5 beta and a host of other solutions.

What I need to know is this:

**How do I create a custom Ubuntu Installation DVD with all of these apps included already? Preferably an easy method -- such as getting a laptop the way you want it, then somehow creating an install dvd based on the software contained on it already.**

Any help you could provide would be wonderful!

Thank you in advance,

Cinmachina

---

### Post by MarblePanther on 2009-02-28
You can try remastersys:

Here's a guide, it may be helpful:

[http://klikit.pbwiki.com/Remastersys+tutorial+by+dedoimedo](http://klikit.pbwiki.com/Remastersys+tutorial+by+dedoimedo)

---

### Post by Fenris_rising on 2009-02-28
I used remastersys to create a backup ISO of my machine. It's great!
There is a limitation in that the resulting ISO must not exceed 4GB
Other than that no problem at all. They have a good forum as well if
you get stuck.

regards

Fenris

---

### Post by cinmachina on 2009-02-28
Thanks for the info guys! I've got it installed and will go to work on this soon. I hope I don't go over 4gig....I think that might be the trouble.

Thanks,

Cinmachina

---

### Post by Fenris_rising on 2009-03-02
You can specify folders/locations to exclude from your image. I would suggest you exclude games, audio, and video. Perhaps save these off seperately? For me it has been a boon to use. Once I had the OS tweaked visually and a 'few' additions to my setup I made a bootable USB stick that in the event of serious problems means I can re-install 'my' OS in 20 odd minutes and continue on my way. Or run the stick as a live 'disk'. You can add a persistent partition to it if theres enough space.

unetbootin can use the ISO to make the USB stick or you can burn the image to a cd/dvd also in 8.10 there is a 'create usb stick from image' type thing in the system>administration menu which can do the same job as unetbootin.

Do see the remastersys forum and wiki for further guidance.

regards

Fenris

---

