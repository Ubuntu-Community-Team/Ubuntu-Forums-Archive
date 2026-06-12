---
title: "Rotating Compiz Cube background"
date: 2009-04-13
forum: Desktop Environments
---

### Post by Rofii on 2009-04-13
How do I make my background rotate along with the cube? I've googled around but can't find anything on it. See 2:40 on this youtube vid if you don't know what I mean: [http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)

---

### Post by OldManRiver on 2009-04-13
R,

If you have latest release/version, Compiz is part of the Ubuntu addons in the "Synaptic Package Manager".

After install you have to click "System" + "Preferences" + "Compiz Settings Manager".

There are HOWTOs at:

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

[http://technetz.com/index.php/2008/07/11/how-to-install-compiz-fusion-in-ubuntu/](http://technetz.com/index.php/2008/07/11/how-to-install-compiz-fusion-in-ubuntu/)

[http://fosswire.com/post/2007/7/how-to-compiz-fusion-on-ubuntu-704-feisty-fawn/](http://fosswire.com/post/2007/7/how-to-compiz-fusion-on-ubuntu-704-feisty-fawn/)

and others, just search google with "howto compiz fusion install ubuntu".

One of the things you will encounter in this install is the "blacklist" of video controllers not supported for this app.  The system basically queries your video card for chipset and RAM and if either doesn't work, blacklists your install and does not let you get to the cube/sphere mode.

There are HOWTOs on how to get around these, but one thing is left out.  If you RAM is limited and it is the reason for the blacklist, you can define/allocate space on your MB RAM for video and cheat, but I still have not found the HOWTO on that, so got caught halfway between and now have to reset my X-Win to default and looking for the HOWTO on that, as now my desktop is totally hosed and unusable.

In other words, be careful with this install, it is tricky and can mess you up good.

Also if you are wanting the Apple/MAC app bar that goes across the bottom of the screen you need to look up the Emerald theme for Compiz and install.  There are also a couple more but not familiar with them.

Cheers!

OMR

---

### Post by Rofii on 2009-04-13
Thanks :)

---

### Post by Jakey_TheSnake on 2009-04-13
Under "Desktop Cube" or "Rotate Cube" there will be an option entitled Skydome. Enable it, choose your image, and select Animate Skydome. 

Regards, 

Jake

---

### Post by OldManRiver on 2009-04-14
J,

Since you know a little about this, and I got stuck where the:

```
sudo dpkg-reconfigure xserver-xorg
```

Command does not recover me.

All my apps go to 0,0 (upper left corner of the screen) and I can not even use anything needing input, such as the FF browser as the input fields are all locked and none of the screen have the upper banner, that lets you move them, so all are stuck at position 0,0 and they pile on top of each, not allowing any nav from app to app.

I hate to have to do a complete rebuild on this machine.

OMR

---

