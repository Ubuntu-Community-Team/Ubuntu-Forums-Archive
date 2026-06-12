---
title: "has any one succesfully installed counterstrike source through wine on a dell e520n"
date: 2007-08-02
forum: Dell  Ubuntu Support
---

### Post by jacob01 on 2007-08-02
yea

---

### Post by Rocket2DMn on 2007-08-02
I play counter-strike 1.6 on my dell 600m.   I followed this tutorial, but I think I got wine from the repos.  Don't forget to install the tahoma font
[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)
I use wine 0.9.39 which can be downloaded as a deb from wine's website because I had a sound lag delay in later versions.  Also, it might help to turn off Beryl/Compiz-Fusion when you play to get a better framerate

---

### Post by jacob01 on 2007-08-06
yea i know im not stupid its a little bit more complex than you think

---

### Post by Rocket2DMn on 2007-08-06
> **jacob01 said:**
> yea i know im not stupid its a little bit more complex than you think

I don't recall ever mentioning or implying that you were stupid.  You asked if anybody had gotten cs to work and I showed you a way that worked for me.  Is there a particular question you have regarding getting cs setup?  I'd be happy to help you troubleshoot.

---

### Post by jacob01 on 2007-08-06
> **Rocket2DMn said:**
> Don't forget to install the tahoma font


yea i never said you did
i didnt forget

---

### Post by Rocket2DMn on 2007-08-06
OK.  I just mentioned it because I said that I installed from the repos rather than using their method, and the tahoma font is mentioned in the wine install portion of the guide.  Just didn't want you to overlook it (this is rather common).
Is everything working well then?

---

### Post by jacob01 on 2007-08-06
yea i see what your saying

---

### Post by jacob01 on 2007-08-06
its just making me mad people telling me that i have driver issues or that i have buggie driver

i am also running an intel g965 chipset wich i guess doesn't have work to good with the drivers

---

### Post by Rocket2DMn on 2007-08-06
I understand your frustration - video drivers are currently one of the biggest problem with linux.  Companies aren't releasing open source drivers for their video cards as much as we would like so it falls to others to try and make adequate drivers.  nvidia and ati have released binary drivers (closed source) that tend to help some people out, but they are imperfect.  Wine is also far from perfect, but it is a developing project with constant updates.  I settled on wine version 0.9.39 because it works best for me since I had a sound delay in later versions when playing counter-strike 1.6.

---

### Post by jacob01 on 2007-08-06
yea are you good with this type of stuff?


if so do you think you could help me to get css workin

my probplem is when i launch css it goes into the css menu and freezes without any text on screen   but it locks up so it isnt a text issue people think its a driver issue wich i probably is so i made a strace or a log but i cant read the log  are you good with that type of stuff

---

### Post by Rocket2DMn on 2007-08-06
If you have a log, please post it.

You can force CS:S to load with certain video settings, other than the ones declared under the video options in the game such as adding "-width 1024 -height 768".  You can add these options by going right clicking the game in steam, hitting properties and looking under the launch options tab.
If you are able to get into the game and navigate the menus, you can choose the correct video options.  Then close cs:s and remove the launch options we added, and reload the game to use the video options you set in game.

---

### Post by jacob01 on 2007-08-06
yea i tried to force a dx level didnt work


i posted my log on 

[http://pastebin.com/m20a24d0](http://pastebin.com/m20a24d0) 

this is not the entire thing this is just the last couple pages

to get this i ran

strace -f -o ~/strace.log wine 'c:\Program Files\steam\steam.exe'

---

### Post by Rocket2DMn on 2007-08-06
I was never able to get my cs 1.6 to run with direct3d, most likely because directx is a windows thing with limited support in linux.  I think many other users have had this problem, too.  Have you tried forcing OpenGL or even just Software mode to see if it runs?  I run with OpenGL using the launch option "-gl"

---

