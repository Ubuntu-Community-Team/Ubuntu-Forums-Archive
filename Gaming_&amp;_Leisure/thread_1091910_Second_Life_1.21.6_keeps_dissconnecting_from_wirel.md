---
title: "Second Life 1.21.6 keeps dissconnecting from wireless network"
date: 2009-03-09
forum: Gaming &amp; Leisure
---

### Post by Zachs Kappler on 2009-03-09
Well after I got a new computer I decided to load the SL Linux client to it and play. This worked fine until I was told/forced to have Vista installed as well. I hate Vista and decided to make the computer dual-boot so I can keep away. Installed SL and after a minute or so it just kills it's internet connection. But not just it's own, every internet connection.the laptop has running! Making me either restart or reconnect to the wireless router. This is getting old fast and I would love to get it working again. I'm running Ubuntu 8.04 since it works well and came with the laptop in question.

---

### Post by Naiki Muliaina on 2009-03-10
How did you install the client? Who told you to use Vista?

---

### Post by hikaricore on 2009-03-10
Just a guess here...I'm thinking the OP needed to run some Windows software title that would not run under WINE.
The OP having a dual boot system is not even relevant to this discussion so lets just ignore that part.

I highly doubt that SecondLife is what is causing the trouble with your wireless connection unless you're pulling too much power from the system's power supply or something strange like that.
Try disabling desktop effects when running games such as second life and see if it makes any difference.
More likely there is something wrong with your wireless network that we're unaware of here.

---

### Post by Zachs Kappler on 2009-03-10
Well my college said I needed office 07, since a copy of XP 64-bit isn't around I was stuck with vista... ANYWAY I figured it out. (Or postponed the disconnect by fixing a update issue...) Seems it messed up getting the newest kernel and left it behind yet updated everything else. Fixing this with synaptic solved it easily. Install the client? You etract it to a folder and are done...

---

### Post by Naiki Muliaina on 2009-03-10
Theres 3 clients for Linux and 1 has a repo :) Didnt know if you had missed some dependencys ^^

---

### Post by Zachs Kappler on 2009-03-10
Well, the kernel made it work fine once... Now it freezes in place randomly and shows zero bandwidth downstream. I'm using the LL viewer. Might try deleting and downloading it again.

---

### Post by RaiCoss on 2009-03-10
> **Zachs Kappler said:**
> Well after I got a new computer I decided to load the SL Linux client to it and play. This worked fine until I was told/forced to have Vista installed as well. I hate Vista and decided to make the computer dual-boot so I can keep away. Installed SL and after a minute or so it just kills it's internet connection. But not just it's own, every internet connection.the laptop has running! Making me either restart or reconnect to the wireless router. This is getting old fast and I would love to get it working again. I'm running Ubuntu 8.04 since it works well and came with the laptop in question.

Why would anyone want to "play" this piece of crap?? It's the most pathetic excuse for a game I've ever come across ¬¬

---

### Post by Zachs Kappler on 2009-03-10
> **RaiCoss said:**
> Why would anyone want to "play" this piece of crap?? It's the most pathetic excuse for a game I've ever come across ¬¬

Griefer, if you don't like it, then look away, I didn't make you read this thread. Plus SL is a social network with a 3D world. It's not a game but many consider it playing when using it like I do.

---

### Post by ubuntu27 on 2009-03-11
> **RaiCoss said:**
> Why would anyone want to "play" this piece of crap?? It's the most pathetic excuse for a game I've ever come across ¬¬

In reply to your question at thread number [1092993]("http://ubuntuforums.org/showthread.php?t=1092993")

First thing, I am not a mod. I will just write what I think.

Your sentence "Why would **anyone** want to "play" this piece of **crap**??..." can be considered an _indirect_ attack on the individual, for you have expressed an opinion that the software in question is crap and individuals using it are unreasonable. 

That's one way people can read your sentence.

Since you feel that you did nothing wrong, I conclude that that was not your intention. You were just expressing your dislike for the software and not the individual. 

_You just chose the wrong set of words_


Next time, just be careful.

---

### Post by Naiki Muliaina on 2009-03-11
To those having troubles theres a repo for the Omvviewer for Second Life. Its not a huge difference but can at least make sure you have all your dependencies in place.

**[Click here for Omvviewer repo]("http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/")**


> **RaiCoss said:**
> Why would anyone want to "play" this piece of crap?? It's the most pathetic excuse for a game I've ever come across ¬¬

It appeals to artistic people who want to create things, business minded people who see there is RL money to be made there. To music fans, there are clubs such as the one i work in (work being a lose word ^^ ) where people DJ and play live music. It has a lot of good educational areas with tutorials ranging from GIMP and Blender to setting up a shoutcast server and meditation. On the subject of education there are a number RL colleges and university's that have courses on SL.

Then for the gamers, there are plenty of good role-play Sims ranging from fantasy to steampunk to futuristic. Some have modern day vampires and werewolves, others have dragons and elves, others have big guns. Also there are combat Sims that play like Quake style games.

Thats why a lot of people like playing this game. Numbers never mean much to me, but by the last count there was 9 million players. If your a numbers fan that may mean something to you.

---

### Post by Naiki Muliaina on 2009-03-11
Quick afterthought on the freezing. Whats your laptops specs and what drivers are you using? There seems to be a long list of complaints with the Nvidia 177 drivers. That could be your freezing problem.

---

### Post by Zachs Kappler on 2009-03-11
Laptop model: Dell XPS M1530
CPU: Intel Core 2 Duo T9300 @ 2.50GHz 2.50GHz (This how it read when I looked it up)
Memory: 4GB (No idea what brand)
GPU NVIDIA GeForce 8600M GT 256MB
Bluetooth: Yes
Wireless: Intel PRO/Wireless 3945ABG
HDD: Hitachi HTS543232L9A300 320GB setup for dual booting
Biometric reader: Yes
CD/DVD: Optiarc DVD+-RW AD-7640A
Webcam: yes
Chipset: Intel ICH8 Family

Side note: I had to add the i8042.noumx=1 setting to my GRUB bootloader so the mousepad functioned correctly in Ubuntu 8.04 but have no idea what all it did.

Open Metaverse Viewer gives me login issues because of something time related.

I experimented with letting my normal LL viewer run without my input... It never seized up or killed the connection until I decided to move around and use it, I think it's mocking me...

---

### Post by Naiki Muliaina on 2009-03-12
Ack :( Silly omvviewer!

Well, you have an Nvidia, what driver are you using? If it is 177 you may need to change to either the newer one or older one (both are in the repos).

---

### Post by Zachs Kappler on 2009-03-12
> **Naiki Muliaina said:**
>  Well, you have an Nvidia, what driver are you using? If it is 177 you may need to change to either the newer one or older one (both are in the repos).
Took some doing since hardware drivers doesn't tell me anymore, but Nvidia X Server Settings tool said it's using the 169.2 driver. The hardware tools says 169.2 IS the newer one...

---

### Post by Zachs Kappler on 2009-07-12
Well the latest copy of GreenLife Emerald fixed this and 9.04 possibly squashed this bug flatter than soda that was open for a month. If it resurfaces I'll gather the new information on it.

---

