---
title: "Doom 3 for linux"
date: 2008-04-05
forum: Gaming &amp; Leisure
---

### Post by linuxguymarshall on 2008-04-05
Where can I download DOOM 3 Linux from the internet? I am not sure how steam works so IDK if I want to use Steam. I would really like to pay $20, download, install and play instead of having to have a cd shipped to me.

---

### Post by metalf8801 on 2008-04-05
look at number 2 on this site [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

---

### Post by linuxguymarshall on 2008-04-05
Are these legal files? I would think that I would have to pay for the Linux version just as I would a Windows version and these seem to be illegal Because I also see Enemy Territory : Quake Wars which is defiantly not free.

---

### Post by Perfect Storm on 2008-04-05
Yes, they are legal - The site contains demo, patches and linux installer. But you still require the CD/DVD to make it work.

> A licensed copy of Doom III retail for Windows
In order to play the additional Resurrection of Evil Expansion Pack, a licensed copy of the Expansion Pack for Windows

---

### Post by linuxguymarshall on 2008-04-05
So I need to buy a Windows install cd? If I do then can someone explain how steam works? Does it give me an executable? An ISO?

---

### Post by Sockerdrickan on 2008-04-05
You buy DOOM 3 at a regular store then install DOOM 3 with the Linux installer, then place some of the files from your CD's to your installation.

---

### Post by FrozenFox on 2008-04-05
Steam has to run in wine because it has no native port that i'm aware of, and will screw up your D3 performance as such if it even runs at all. Just buy the cd somewhere and use the native linux installer. You probably wont find a place to e-download it legally how you want.

---

### Post by Dark Aspect on 2008-04-05
> **FrozenFox said:**
> Steam has to run in wine because it has no native port that i'm aware of, and will screw up your D3 performance as such if it even runs at all. Just buy the cd somewhere and use the native linux installer. You probably wont find a place to e-download it legally how you want.

Can you even buy Doom 3 off Steam????I thought that was only games like Counter Strike and stuff.

---

### Post by aoanla on 2008-04-06
> **Dark Aspect said:**
> Can you even buy Doom 3 off Steam????I thought that was only games like Counter Strike and stuff.

No, Steam now provides all of id Software's back catalogue, all of Epic's back catalogue, quite a lot of Take 2 Interactive's stuff, and tons more games from lots of publishers.

---

### Post by NR1224 on 2008-04-06
im not sure, but i believe that steam is a content delivery service. I theory, when u download the game, you should aquire the 5 .pk4 files you need. Be careful though, i really dont have any idea if the download will contain the files at all.  A used copy is most like ky your best be. Try amazon or ebay

---

### Post by jjk7288 on 2008-04-06
I've done this before.

Follow the directions on [http://zerowing.idsoftware.com/linux/doom/]("http://zerowing.idsoftware.com/linux/doom/") and then download Doom 3 from Steam. Navigate to Doom 3's directory and find the .pk4 files that the guide talks about.

I haven't had any problems.

---

### Post by Ninja Krow on 2008-10-10
I just tried this out for myself with my copy that I got on the Release day for Doom3. Surprised that my copy still worked I grabbed the Files off each of the 3 CDs in the set and put there in "/usr/local/games/doom3/base" Like the Readme told me to and what do you know. Had to make sure the permissions where all set to read/write but once I used "Sudo cp 8.pk4 /usr/local/games/doom3/base" in my Terminal and copied them all over. All as good and it ran like a dream. 

Wasn't too comfortable about plugging my root password into it but It actually ran that way. I couldn't get it to even run from my user account in my home folder.

Now I trying to remember what happens when I shine my Flash Light in the Bathroom Mirror that first time. I know something happens... Do they give me a Puppy and say "For The Win!..."

By the way thanks for hooking me up with the Initial Web Site that got me to try this. I am now going to try it with the Quake4 CD edition.

---

### Post by Twohanzos on 2008-10-11
Could anyone explain to me (maybe in email or ubuntuforum messages) how exactly to get windows games working on ubuntu. Ive never played doom or quake but form what they read they sound kool. Id also like to know how to play mmorpgs and stuff on linux. Please if anyone could help me?

---

### Post by Jim! on 2008-10-11
> **Twohanzos said:**
> Could anyone explain to me (maybe in email or ubuntuforum messages) how exactly to get windows games working on ubuntu. Ive never played doom or quake but form what they read they sound kool. Id also like to know how to play mmorpgs and stuff on linux. Please if anyone could help me?

You can get some Windows games to work under Linux using Wine. [http://en.wikipedia.org/wiki/Wine_(software](http://en.wikipedia.org/wiki/Wine_(software))

To install wine just type the following in a terminal:

```
sudo apt-get install wine
```

---

