---
title: "Doomsday Issues"
date: 2006-08-19
forum: Gaming &amp; Leisure
---

### Post by aglc2005 on 2006-08-19
Hi I have succesfully installed the Doomsday engine (deng) along with all the WADS using the installers. I have also installed the deng-jdoom-rp-core and deng-jdoom-sycraftsdoommusic. The last package installed was a failed attempt to get the music playing. After reading through the read me for deng-jdoom-sycraftsdoommusic it says that I have to activate it in Kickstart. From my understanding kickstart does not work on a Unix system (I am running Ubuntu 6.06 LTS Dapper). So my question is how would get music to play, I have sound effects just no music?

I also have gDoomsday installed to give me a gui.

---

### Post by Sandlst on 2006-08-19
Just to be sure, have you installed the recommended packages for deng? (timidity and freepats)?  Im not sure if they are necessary for music playing with that music pack, but I know for me they are without the music pack.

---

### Post by aglc2005 on 2006-08-19
I was using [this]("http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu")
website for what i needed and did not see it listed on there, what is the name of the package(s).

---

### Post by jason.b.c on 2006-08-19
I want this too , What do i do to get it..???    Terminal command..

It's a .deb right..?

---

### Post by HAARP on 2006-08-19
I bet you're using Yagi's Breezy repos? Just change it to Dapper to get the newest version. However, it's still unstable (As is the Breezy version)
Sycraft's stuff will be available soon for Doom.

---

### Post by Sandlst on 2006-08-19
For those interested, the command that got my music up and running was ```
sudo apt-get install timidity freepats
```

---

### Post by aglc2005 on 2006-08-20
> **Sandlst said:**
> For those interested, the command that got my music up and running was ```
sudo apt-get install timidity freepats
```

Hey thanks that worked beautifully, and the music that I have is just down right awsome\\:D/

---

