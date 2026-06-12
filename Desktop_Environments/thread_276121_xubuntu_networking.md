---
title: "xubuntu networking"
date: 2006-10-12
forum: Desktop Environments
---

### Post by studiesrule on 2006-10-12
After a good install off the live cd, I noticed two things:
1. Whenever I open an adminstrative screen, i.e. networking, login settings, etc. it does not ask me for root password.
2. I'm not able to get my networking settings to stay.
Basically, I enter in my static IP, netmask, and gateway. I also added my DNS, but the tick mark at the top of the window doesn't open (I'm assuming its apply). I close the window, but the gateway settings don't stay. As a result, I'm able to login into my ISP, but I can't use anything.

I'd also like to ask about the generic programs for the Xfce env.

Multimedia: I'd like something like RhythmBox (or Amarok if it's possible)
Development: Something like Anjunta of KDevelop
Torrenting: like Gnome's BitTorrent

Thanks for the time

Specs: Compaq Presario SR173IL: P4 3.06 GHz, 256MB DDR-2 RAM, Generic Realtek RT8139L LAN Card (I access my net through this)

---

### Post by dannyboy79 on 2006-10-12
> **studiesrule said:**
> After a good install off the live cd, I noticed two things:
1. Whenever I open an adminstrative screen, i.e. networking, login settings, etc. it does not ask me for root password.
2. I'm not able to get my networking settings to stay.
Basically, I enter in my static IP, netmask, and gateway. I also added my DNS, but the tick mark at the top of the window doesn't open (I'm assuming its apply). I close the window, but the gateway settings don't stay. As a result, I'm able to login into my ISP, but I can't use anything.

I'd also like to ask about the generic programs for the Xfce env.

Multimedia: I'd like something like RhythmBox (or Amarok if it's possible)
Development: Something like Anjunta of KDevelop
Torrenting: like Gnome's BitTorrent

Thanks for the time

Specs: Compaq Presario SR173IL: P4 3.06 GHz, 256MB DDR-2 RAM, Generic Realtek RT8139L LAN Card (I access my net through this)

Sounds to me like you DON'T have a good install. 

1. I use Xubuntu on my laptop and it always asks me for a root password when doing the things you mentioned and it does that by default without my changing any settings, so I am not sure how you would fix that if you are concerned that someone besides you uses your comp and you are afraid they may screw it up.
2.  The networking gui sounds to me like it is messed up somehow, i am not sure what you mean about some tick mark. You could always enter all this info in manually into the files themselves. I believe they are /etc/network/interfaces (that'll be for your ip and netmask and gateway) then there is i think nsswitch or something like that you can just edit those using mousepad. You'll have to either wait for me to respond AFTER i get home. i can tell you how to enter the info and what not or retart and see if the networking gui works better.

Bittornado is what I use for my torrent client, I downloaded 0.3.15 I believe and installed that one cause the torrent site I belong to wouldn't accept the one that get's installed with aptitude install. Multimedia, there should be no reason why you can't install either one of those that you mentioned it's just that they'll add a lot of dependcies and fill up your computer. I use xmms. it's pretty sweet but since I haven't used Rythmbox or Amarock or whatever, I can't tell you if ones better than the other. As far as Development, cvan't help you. i am just a linux newbie. Good luck, i'll come back here adn see if you got your networking issue resolved and if not, i'll post how you can update the files manually so that your internet settings stick. Good luck and welcome to xubuntu!

---

### Post by studiesrule on 2006-10-12
Thanks for the prompt reply (just 12 min. or something) Ok:
I've used ubuntu and kubuntu, and both work perfectly fine. However, due to my pathetic ram, they slow up too much. By good install, it didn't pop up any messages. I've tried to modify the interfaces file using sudo nano -w /etc/networking/interfaces, and have added the line:
gateway 172.30.0.1
It doesn't work though. I checked later, the file is unchanged, but it hasn't appeared in the networking window when I restarted.
By tick mark, I refer to a small button at the upper right corner of the networking (which is only a tick mark).

I've heard about XfMedia for a media player.

---

### Post by studiesrule on 2006-10-12
RESOLVED!!!
I got it working (I'm not fully sure how). I basically tried changed my interfaces file in several ways trying to see what worked, and restarted my device several times. Finally it worked. Thanks for the help anyway.

---

### Post by dannyboy79 on 2006-10-12
> **studiesrule said:**
>  I've tried to modify the interfaces file using sudo nano -w /etc/networking/interfaces,
Just so you know XFCE, which is the Window Manager that Xubuntu uses, (similar to Gnome for Ubuntu and KDE for Kubuntu) has Mousepad which is WAY better than nano but of course it's your choice. Just letting you know cause you can copy and paste in Mousepad and in nano you can't.
> **studiesrule said:**
> I've heard about XfMedia for a media player.
Yes, that's what's installed by default. XMMS is better though I can tell you that much! Again, just my opinion. Good luck

---

### Post by xeero on 2006-10-12
You can find some recommended xfce apps here:
[http://www.xfce.org/index.php?page=links&lang=en](http://www.xfce.org/index.php?page=links&lang=en)

I've tried xfmedia to play video and it seems much more efficient (fast) than the other major players.  I believe it's still in beta stage right now.  For audio, Amorak has better sound than xmms.. not sure if it's possible to change the engine for xmms.  

For software dev, I use Eclipse IDE.  It's not lightweight, but it's comprehensive and widely used (hence, lots of support).

---

