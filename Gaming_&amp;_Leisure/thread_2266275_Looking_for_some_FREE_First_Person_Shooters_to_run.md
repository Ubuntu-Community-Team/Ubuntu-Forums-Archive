---
title: "Looking for some FREE First Person Shooters to run on ubuntu."
date: 2015-02-21
forum: Gaming &amp; Leisure
---

### Post by mandarpowale on 2015-02-21
Hi,

I would like some recommendations regarding Free First Person Shooters to run on UBUNTU.

TY in advance.


Mandar Powale

---

### Post by pqwoerituytrueiwoq on 2015-02-21
[http://www.xonotic.org/](http://www.xonotic.org/)

[http://www.playdeb.net/updates/ubuntu/14.10/?q=xonotic](http://www.playdeb.net/updates/ubuntu/14.10/?q=xonotic)

---

### Post by bizhat on 2015-02-21
Team Fortress 2.

If you can pay, get Counter Strike Global Offensive, work properly on Ubuntu, you can get it cheap on steam sales.

---

### Post by mandarpowale on 2015-02-21
OK thanks for your replies. I will check everything out ASAP.

I do have CS Anthology.

I was looking for Single-Player FPS.

---

### Post by pqwoerituytrueiwoq on 2015-02-22
xonotic has a single player mode, but playing bots does get boring, still good for practice before you use online play

---

### Post by zathras1974 on 2015-02-22
A quick search of the software center should give you more results than you can shake a stick at. ;)

If you use AppGrid (I like it), it will also give you the ability to sort by popularity.

Happy hunting, in both senses of the word. 

~Z

---

### Post by drarem2 on 2015-02-22
Myself and someone else are working on a $1 game, although not ready to release alpha yet.

[https://www.kickstarter.com/projects/1367196571/pump-action-captain](https://www.kickstarter.com/projects/1367196571/pump-action-captain)

---

### Post by Li_Wu on 2015-02-22
sauerbraten

fps shooter extraordinaire

---

### Post by mateo14 on 2015-02-22
Aliens vs Predator is the cheap game, and you can install the Classic Redux Mod if you want to have the game that is similar to modern FPS games:

[http://icculus.org/avp/](http://icculus.org/avp/)

[https://www.youtube.com/watch?v=YGhbIirRSho](https://www.youtube.com/watch?v=YGhbIirRSho)

---

### Post by mandarpowale on 2015-02-23
Thanks to all of you ...

---

### Post by oldrocker99 on 2015-02-23
As these replies show, there are (and have been for years) a ton o' shooters for Linux, FOSS and closed-source (quite a few on Steam, as well).

If only RTS games were as well-represented. The current (IMHO) champ is Planetary Annihilation, available on Steam. It, among other things, allows planets to be smashed into other planets. Oh, well. I have so many games in my Steam account that sometimes I have to visit the store game page to remind me of the game:oops:.

---

### Post by mandarpowale on 2015-02-24
I may be asking for too much but I downloaded Xonotic and have extracted the zip file, but how to install it or start it? I also installed Sauerbraten which was easier since it is present in Ubuntu Software Center.

Add: Do I need wine, since there seems to be a Xonotic.exe file ?

---

### Post by pqwoerituytrueiwoq on 2015-02-24
just run this file (the highlighted one), btw xonotic is in the software center and in the [playdeb]("http://ubuntuforums.org/www.playdeb.net/updates/ubuntu/14.10/") repo
[[IMG]http://www.zimagez.com/miniature/screenshot-02242015-074445pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-02242015-074445pm.php")
here are command line install instructions for playdeb/xonotic
```
echo "deb http://archive.getdeb.net/ubuntu $(lsb_release -sc)-getdeb games" | sudo tee -a /etc/apt/sources.list && wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
sudo apt-get update && sudo apt-get install xonotic
```

---

### Post by mandarpowale on 2015-02-25
^^ Ummm, I'm using UBUNTU 14.04 LTS which might be why I did not find Xonotic in the 'software center'.

---

### Post by oldrocker99 on 2015-02-25
```
apt-cache search xonotic
darkplaces - Game engine for Quake and similar 3D first person shooter games
darkplaces-server - Standalone server for Quake-based games
libd0-blind-id0 - library for user identification using RSA blind signatures
libd0-blind-id0-dev - library for user identification using RSA blind signatures (headers)
[b]xonotic - Fast-paced first-person shooter
xonotic-data - Fast-paced first-person shooter (data package)[/b]
```

Oh, it most certainly is in the repositories. Install it, no muss, no fuss, thus:
```
sudo apt-get install xonotic
```

It will return:
```
 [sudo] password for {user}: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libd0-blind-id0 xonotic-data
The following NEW packages will be installed:
  libd0-blind-id0 xonotic xonotic-data
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 925 MB of archives.
After this operation, 946 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

That's all there is to it. You can also use that command to install synaptic, which is a highly-recommended software installer. The Software Center has some advantages, but it pales in usefulness and speed to synaptic.

As you see in the first example, the **apt-cache search** command can list any program or library name (or anything else) you can think of, which can also save time. One of the great things about Linux is the different ways you can accomplish tasks.

---

### Post by KyleG545 on 2015-03-01
Urban Terror might be worth a look i havnt played it in forever though.
[http://www.urbanterror.info/home/](http://www.urbanterror.info/home/)

---

### Post by mandarpowale on 2015-03-03
> **zathras1974 said:**
> A quick search of the software center should give you more results than you can shake a stick at. ;)

If you use AppGrid (I like it), it will also give you the ability to sort by popularity.

Happy hunting, in both senses of the word. 

~Z

AppGrid not present in the software center ? Also will it work on 14.04, because the website says 14.04+?

---

### Post by oldrocker99 on 2015-03-03
> **mandarpowale said:**
> AppGrid not present in the software center ? Also will it work on 14.04, because the website says 14.04+?

You are already running a later version that 14.04, which is currently 14.04.2. No worries there. This version will be fully supported until 2019.

Now, to add the online repository that you can download AppGrid from, do this in the terminal:```
sudo apt-add-repository ppa:appgrid/stable
sudo apt-get update
sudo apt-get install appgrid
```

That should set you up. Let us know if it worked.

---

### Post by mandarpowale on 2015-03-04
At the end of third command, this is the output i get.

> stop: Unknown instance: 
appgrid stop/waiting
OK
mandar@Mandar-PC:~$ 


Does it mean that the service was installed successfully or not ? I think it means that the service was installed successfully but just not started because Ubuntu doesn't trust it. Am i right ? I can't use Synaptic because I am a novice at Linux as such.

Off:Topic : Will you tell me the command to run the equivalent of task manager?

---

### Post by oldrocker99 on 2015-03-04
Look in your menus (or in the Dash) for "Syetem Monitor."

Synaptic is easier to use than you think. If it isn't installed,```
sudo apt-get install synaptic
``` will set you up.

Once it's installed, start it from the icon. You'll be asked for your password for it. Then, there's a Quick Filter box as well as a more thorough Search feature. The Quick Filter box will allow searching for an app by name. The Search function is for that, as well as finding a group of apps, like music players, from which you can select one or several of the apps and install them at one time, instead of one at a time the way the Software Center installs them. 

Synaptic was the way I learned to install software when I was a novice, and I figured it out, so I'm pretty sure that you can, as well!

---

### Post by mandarpowale on 2015-03-04
> **mandarpowale said:**
> At the end of third command, this is the output i get.

Does it mean that the service was installed successfully or not ? I think it means that the service was installed successfully but just not started because Ubuntu doesn't trust it. Am i right ? I can't use Synaptic because I am a novice at Linux as such.

Off:Topic : Will you tell me the command to run the equivalent of task manager?

Edit: The application App Grid, is not working properly. Even though I found and ran it from Dash. Also there is no icon on the unity bar. I can't find the install button.

---

