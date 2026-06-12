---
title: "Why does it always have to rain on me? :)"
date: 2006-03-08
forum: Desktop Environments
---

### Post by Low Rider on 2006-03-08
Hi, everyone!

I just installed Breezy and it always keeps the same thing: when booting, system freezes for a long while when it comes to configuring network. After that, it gives up and continues the booting process.
Once in KDE, whenever I try to do something involving the network, it says it can detect my devices but isn't able to switch them on (or something like that). I go to KControl and try to put DHCP to work but it always fails. 
Of course, I'm no "power-user" so I went looking for possible solutions but all of them (which involved checking several network-related config files) haven't been effective at all. I really would like to give Ubuntu a go, but it's bugging my brains off! Gentoo is also an option (I prefer distros with original packaging systems) but it does have a rather tiring installation process...
Is there anyone around who can help me? My eternal gratitude! :D


Hugs & kisses for everyone! ;)

---

### Post by Lord Illidan on 2006-03-08
Welcome to the forums, Lone Rider. Mind if you give us details on your network hardware? Is it wireless?

Also, during bootup, if it freezes again, press CONTROL + C

---

### Post by Single on 2006-03-08
I also experienced this. It was because KControl generates invalid config file.
Your case is probably the same.
I am no expert in this, but I try to help as much as I can.

Which network interface(e.g. eth0, eth1...) do you want to turn on DHCP? 
Try this in Konsole (substitute eth0 with other, if yours is different):
```
sudo ifdown eth0
sudo ifup eth0
```

---

