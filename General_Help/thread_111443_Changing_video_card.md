---
title: "Changing video card"
date: 2006-01-02
forum: General Help
---

### Post by PriceChild on 2006-01-02
Hey, i'm currently running a Geforce 4 MX 440 SE 128mb Ram

I've got the nvidia drivers installed, however, i'm going to be swapping to a GeForce4FX 5600

What things special must i do to change over without problems?

---

### Post by Dr. Nick on 2006-01-02
Shouldnt have to change anything as long as they are both nvidia and both use the same bus. You can edit your xorg.conf to change the identifier for your card.

---

### Post by Omnios on 2006-01-02
Think about the only thing you have to do is your xorg as stated and sudo nvidia-glx-cconfig enable which  is  what I did a few months back when I got a new vid  card. It configs your xorg for you cand  I think.

---

### Post by futz on 2006-01-02
If you restart your machine after the hardware swap and it won't boot to the gui, but instead drops you into a text terminal screen (happened to me when I changed vid cards), just login and run 
```
sudo dpkg-reconfigure xserver-xorg
```

If you don't know the answer to a question in this tool, usually you can just hit <Enter> to accept defaults and it'll be ok. When you finish the reconfigure type 
```
startx
```
to test the X server. If it doesn't work then try again, but do something different this time. 

I've had to run it like 3 times in a row till I got the setting it was choking on right, and even then had to edit xorg.conf to get it exactly how I wanted it. But the new card is great! :mrgreen:

---

