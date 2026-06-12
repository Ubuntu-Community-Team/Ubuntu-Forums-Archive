---
title: "Allot of noob problems :("
date: 2009-03-23
forum: General Help
---

### Post by Daxia333 on 2009-03-23
Hi!

I just installed ubuntu, and I have sucefully started up the computer. Now, I have some noobish questions that I hope you can help me with.

1. I have a Dell M1710 and the first thing your supposed to install on a windows os is the "laptop tools" or something like that. Do I have to do something like that with ubuntu?

2. I found the update thing, and it found about 120 updates. I started downloading, but the speed is really slow I have a 4M/B connection and usually, downloads are in 400-450kb/s but when updating the speed is like from 0.5kb/s - 25kb/s. Is there any way to increase the download speed (Im located in China)

3. Now, the resulotion is 800x600 or something like that, but I usually go with 1600x1200. I guess that the video drivers hasnt been correctly installled. Is there some "Automatic hardware update" feature?

4. What will I need to play WoW?

Thanks allot in advance!!!!!!!!!!!!!

---

### Post by ubersolid on 2009-03-23
If it is this laptop [http://www.linlap.com/wiki/Dell+XPS+M1710](http://www.linlap.com/wiki/Dell+XPS+M1710)
then the nvidia drivrs can be installed by going to hardware drivers under System -> Administration. The laptop-tools are installed by default if I remember correctly.
Just finish the updates and possibly reboot before you install any drivers.

---

### Post by Spaarkplug on 2009-03-23
You need to google your issues one by one, there are solutions to all your issues online. I know it may seem frustrating now, but don't worry, we all have been thru this experience which you are having now.
As for your wireless/internet being slow,.. i think (maybe) the Ubuntu did not recogonize your wireless card so the modules ( in ubuntu we call drivers as modules) may not be loaded. Do an 'lspci' to find out your wireless card. and then do an 'lsmod' on your terminal and check if you see your wireless cards name is present there.
You need to install your nvidia drivers. I think it should be installed by default. Try display preferences and play around a little.
WoW, can be played after you install Wine 2.0 on your laptop. It is one of the most explained in detail app installed using wine.
Goodluck!

---

### Post by Lunx on 2009-03-23
> **Daxia333 said:**
> 
2. I found the update thing, and it found about 120 updates. I started downloading, but the speed is really slow I have a 4M/B connection and usually, downloads are in 400-450kb/s but when updating the speed is like from 0.5kb/s - 25kb/s. Is there any way to increase the download speed (Im located in China)


If you open up Synaptic Package Manager by going to **System --> Administration --> Synaptic Package Manager**, you will see a tag called **Settings**, click on that and you will see a menu called **Downloads** where you can set it to a different server to download from. Just make sure you hit the reload button in Synaptic if you change the download location, so that the repositories are updated. I changed my server to one that belongs to my ISP and I don't use any of my download quota for updates or other downloads for ubuntu.

---

