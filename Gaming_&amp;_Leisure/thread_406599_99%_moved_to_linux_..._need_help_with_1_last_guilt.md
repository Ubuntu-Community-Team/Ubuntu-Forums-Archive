---
title: "99% moved to linux ... need help with 1 last guilty pleasure"
date: 2007-04-11
forum: Gaming &amp; Leisure
---

### Post by shan2on_power on 2007-04-11
hey all, 

I've been a slackware user since version 7.3, and a fan of the debian netinstall since it came out. 

Now being lazy and busy with work and what not, i have moved to the ubuntu distro as it has all my apples in 1 basket with less time of manually installing and configuring packages.


anywho.... 
here is my problem, my sql/perl/apache server resides here, and i want to run world of warcraft on linux to make my life 100% windows free.


I got as far as installing the game and installing all the updates, [not yet burning crusade] using wine and the howto at the sticky section of this thread.

everything seems to work until i login.

The fonts are small and the 
> sudo aptitude install msttcorefonts
command does not work. the error that is present it cannot find the resources.

I enabled universe/multiverse repositories and still a no go...

I did however find a .deb download but not sure on how to install .deb's on ubuntu...

almost there could some1 help ? 

greatly appreciated

~ shan2on




oh, Here is some directx/opengl info that is probably needed...
glxinfo
> 
shan2on@magtheridon:~$ glxinfo | grep direct
direct rendering: Yes

glxinfo
> 
shan2on@magtheridon:~$ glxinfo | grep 'OpenGL version'
OpenGL version string: 2.0.2 NVIDIA 87.76


glxgears
> 
shan2on@magtheridon:~$ glxinfo | grep 'vendor'
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
shan2on@magtheridon:~$ glxgears -printfps
9420 frames in 5.0 seconds = 1883.946 FPS
9462 frames in 5.0 seconds = 1892.206 FPS
9468 frames in 5.0 seconds = 1893.404 FPS
9465 frames in 5.0 seconds = 1892.937 FPS
9466 frames in 5.0 seconds = 1893.022 FPS
9465 frames in 5.0 seconds = 1892.868 FPS
X connection to :0.0 broken (explicit kill or server shutdown).


---

### Post by cantormath on 2007-04-11
Tutorial
[http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

---

### Post by shan2on_power on 2007-04-11
> **cantormath said:**
> Tutorial
[http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)



gee, do people even read what i type?

i typed that i used this howto to install it, the problem is with fonts they are too small to read, and when i login to game i cannot read the jumbled text.

I enabled uni/multiverse repositories and still cannot get msttcorefonts to be installed.
 
could this be the reason warcraft is asking me to shutdown or return to login screen ?


any decent help would be appreciated, not a link that i've already reviewed.

thanks

---

### Post by lordhebe on 2007-04-11
Well you can try using the .deb file from here: [http://packages.ubuntu.com/edgy/x11/msttcorefonts]("http://packages.ubuntu.com/edgy/x11/msttcorefonts")
Here is a guide on installing .deb files : [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/install-file.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/install-file.html")

Hope this helps you.

---

### Post by shan2on_power on 2007-04-11
> **lordhebe said:**
> Well you can try using the .deb file from here: [http://packages.ubuntu.com/edgy/x11/msttcorefonts]("http://packages.ubuntu.com/edgy/x11/msttcorefonts")
Here is a guide on installing .deb files : [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/install-file.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/install-file.html")

Hope this helps you.



thanks for your help lord... i installed the package without problems.....

however the same problem persists...

maybe a screenshot would help ?


thanks in advance

~ shan2on

---

### Post by cantormath on 2007-04-11
> **shan2on_power said:**
> gee, do people even read what i type?

i typed that i used this howto to install it, the problem is with fonts they are too small to read, and when i login to game i cannot read the jumbled text.

I enabled uni/multiverse repositories and still cannot get msttcorefonts to be installed.
 
could this be the reason warcraft is asking me to shutdown or return to login screen ?


any decent help would be appreciated, not a link that i've already reviewed.

thanks

I didnt see the name or a link to the thread I mentioned, so I mentioned a thread that was recently posted.  

I guess I just dont care enough to put more thought into a gaming complaint, Sorry :KS

---

### Post by FoolsGold on 2007-04-11
> **shan2on_power said:**
> maybe a screenshot would help ?
Holy hell, I think your WoW client's been smoking some bad weed. :)

I recommend you check out the Wine App DB report for World of Warcraft:

[http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)

Choose your version and off you go. From the looks of things it's a very-well supported game in Wine (understandable - the Wine developers work hard to support popular games), so from the hundreds of comments you should have some luck, hopefully. Good hunting!

---

### Post by shan2on_power on 2007-04-11
> **FoolsGold said:**
> Holy hell, I think your WoW client's been smoking some bad weed. :)

I recommend you check out the Wine App DB report for World of Warcraft:

[http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)

Choose your version and off you go. From the looks of things it's a very-well supported game in Wine (understandable - the Wine developers work hard to support popular games), so from the hundreds of comments you should have some luck, hopefully. Good hunting!

10/10 !!!

i fixed it, thanks for your help fools...

here's what i did...

"-opengl" at the end of my desktop icon's launch command inside it's properties...

thanks for your help.

~ shan2on

---

