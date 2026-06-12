---
title: "cant install 'Spring'"
date: 2009-01-16
forum: General Help
---

### Post by insanity99 on 2009-01-16
i really want to play this game, i went to System > administration > software sources and added the link provided on their site but it still wont find it on the package manager. and the link to download it on the website doesn't work either. 

thnx.

---

### Post by oldos2er on 2009-01-16
Do you have a URL for it?

---

### Post by insanity99 on 2009-01-16
[http://spring.clan-sy.com/](http://spring.clan-sy.com/)

---

### Post by oldos2er on 2009-01-16
Assuming you're running Ubuntu 8.10, add this line:

deb [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) intrepid main

 to your sources (System, Administration, Software Sources, Third party software, Add).
Click Add Source, Reload. It should show up in Synaptic now.

---

### Post by insanity99 on 2009-01-17
> **oldos2er said:**
> Assuming you're running Ubuntu 8.10, add this line:

deb [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) intrepid main

 to your sources (System, Administration, Software Sources, Third party software, Add).
Click Add Source, Reload. It should show up in Synaptic now.

i have added that link but it still isn't there. 

[IMG]http://i304.photobucket.com/albums/nn198/insanity9_bucket/Screenshot.png[/IMG]

that is right isn't it?

---

### Post by oldos2er on 2009-01-17
Yes, that's right. Now click 'Close', you'll be prompted to reload your sources.list. Do that, and you should be able to install the game from Synaptic.

---

### Post by insanity99 on 2009-01-17
thnx, i had to reload twice and get it from terminal. strange.

---

