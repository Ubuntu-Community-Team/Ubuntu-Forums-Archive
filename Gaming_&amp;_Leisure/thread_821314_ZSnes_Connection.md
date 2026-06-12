---
title: "ZSnes Connection"
date: 2008-06-07
forum: Gaming &amp; Leisure
---

### Post by KadFlynn on 2008-06-07
hey guys! I have a question for y'all. I hope I put it in the right spot here. ^_^;;;

I got my ZSNES exe playing in Wine, and I was hoping to use netplay, but I'm having problems connecting. It may very well be my friend's end, but I was wondering if there was anything I could do to make sure that it's not my end. Are there permissions that I can set up to make sure it's not being blocked? I'm using the Windows version of v1.42. I don't know how to get the source to work on Ubuntu, so I'm using wine. Haha. Please help if you can!

---

### Post by slave-zeo on 2008-06-07
Not sure if this will help but you can always do a 

```
sudo apt-get install zsnes
```

and install the native linux version of ZSNES. You can also search for it in Snyaptic and install it via the GUI. ZSNES in the repositioris is version 1.51.

---

### Post by Grishka on 2008-06-07
> **slave-zeo said:**
> Not sure if this will help but you can always do a 

```
sudo apt-get install zsnes
```

and install the native linux version of ZSNES. You can also search for it in Snyaptic and install it via the GUI. ZSNES in the repositioris is version 1.51.

I don't think this will work. netplay is broken since 1.40, with an exception of version 1.42n.

---

### Post by acoustibop on 2008-06-07
I don't think it's broken; it was removed.

FWIW 1.42 was the version provided in the Feisty repositories; some games/software/.debs sites may still offer 1.42 .debs - whether they'll work in Gutsy or Hardy, though, I don't know.

---

### Post by Grishka on 2008-06-07
> **acoustibop said:**
> I don't think it's broken; it was removed.

FWIW 1.42 was the version provided in the Feisty repositories; some games/software/.debs sites may still offer 1.42 .debs - whether they'll work in Gutsy or Hardy, though, I don't know.

yes, it's broken. at least that's what the devs say. [http://board.zsnes.com/phpBB2/viewtopic.php?t=2202](http://board.zsnes.com/phpBB2/viewtopic.php?t=2202)

---

### Post by acoustibop on 2008-06-07
Ah, yes, you're right Grishka - there's still a Netplay option on the menu bar.

---

### Post by KadFlynn on 2008-06-08
Haha. I did see the ZSnes 1.51 in the Package Manager, but I knew the Netplay Didn't work. I have a friend who wrote the FAQ for ZSNES. He has told me that they meant to include it originally, but just didn't. So you guys don't have any advice? Thank you everyone for taking the time out to try to answer my question. It's been appreciated. ^_^

---

