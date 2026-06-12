---
title: "Quake 4 is up to nonsense :("
date: 2010-05-08
forum: Gaming &amp; Leisure
---

### Post by bigseb on 2010-05-08
So here is what I did:

I followed the instructions in this link: 

[http://www.blog.highub.com/linux/install-and-play-quake-4-on-ubuntu/](http://www.blog.highub.com/linux/install-and-play-quake-4-on-ubuntu/)

When I ran that last command (./quake4-linux-1.4.2.x86.run) to run the installer that little box pops up with the installer queries ie where to installer etc. The paths that it suggests don't work, neither do the ones that I created as per instruction in that link. So I created a new folder in my Home directory called games which was accepted. Ran the installer again. 

Now I'm looking for a link to start the game... no link :( So I start browsing through the 'Games' folder (the one I created in the Home dir) - the link is there. Clickety click and suddenly the image on my screen is 4x the size! What I mean is the entire display shows only the top left quarter of the 'image'... I have to scroll the screen to see the entire image... hope I'm making sense...

Also, for a split second it show the 'loading menus' screen of the game then it just reverts to my desktop. The size issue in the above paragraph remains though. 

Help! I can't find what is running that's causing this, or how to fix the display. Only option so far has been to reboot.

Lastly, when I do the said reboot it restarts then just before Grub starts it hangs, I have to ctrl+alt+del to restart then it runs fine. This has only been since I tried to install the game.

Strange thing is that installed quake 4 before and it worked fine but a few days ago I reinstalled the OS and this time its not doing it.

WTH?!?!

---

### Post by Bölvaður on 2010-05-08
the reason you couldnt install the game in some paths is because you didn't run the installer under root. And the user only has access to home, so obviously... that's where you are able to install it. What I do is to have a /data/Games

but ok your display problem :
Look for this file
~/.quake4/q4base/Quake4Config.cfg

and look for this
```
 
seta r_mode "7"
```
you probably have something elset han 7


> seta r_mode "9" = 1600x1200
seta r_mode "8" = 1280x1024
seta r_mode "7" = 1152x864
seta r_mode "6" = 1024x768
seta r_mode "5" = 960x720
seta r_mode "4" = 800x600
seta r_mode "3" = 640x480
seta r_mode "2" = 512x384
seta r_mode "1" = 400x300
seta r_mode "0" = 320x240 


To set a custom mode  you need to change r_mode to -1 and then specify the height and width like this

seta r_mode "-1"
seta r_customheight "1680"
seta r_customwidth "1050"


you dont need to set customheight and width. it's just in case.

---

