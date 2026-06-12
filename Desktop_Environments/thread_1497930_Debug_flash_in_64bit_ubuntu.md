---
title: "Debug flash in 64bit ubuntu"
date: 2010-05-31
forum: Desktop Environments
---

### Post by kamina on 2010-05-31
I've finally managed to (almost) set up my new workstation, but noticed Adobe is not offering a debugger version of flash for 64bit operating systems. Even the alpha of the 64bit normal player does not manage to play back a site that I need quite frequently.

I've read a lot of old posts regarding installing a 32bit i386 firefox, so I assume that's what I should do. Can I just replace the 64bit version completely (and if yes, what would the drawbacks be)?

---

### Post by moongia on 2010-05-31
> **kamina said:**
> I've finally managed to (almost) set up my new workstation, but noticed Adobe is not offering a debugger version of flash for 64bit operating systems. Even the alpha of the 64bit normal player does not manage to play back a site that I need quite frequently.

I've read a lot of old posts regarding installing a 32bit i386 firefox, so I assume that's what I should do. Can I just replace the 64bit version completely (and if yes, what would the drawbacks be)?

I'am not running 64bit,but i have ubuntu-tweak installed,and there an option to install 64bit flash.hope this helps...

---

### Post by lovinglinux on 2010-05-31
Make sure you don't have any other flash plugin installed.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Cavsfan on 2010-05-31
Don't mean to butt in **lovinglinux** as I am sure you know a lot more than I about all of this.

But, I had mentioned I was having problems with flash on youtube videos.
And I opened this thread _[http://ubuntuforums.org/showthread.php?t=1496785]("http://ubuntuforums.org/showthread.php?t=1496785%3Cbr%20/%3E")_

**Spr0k3t **posted a bug report and a workaround for the problem.
I was able to fix my problem just by doing step 3 of the workaround and everything works perfectly for me now.
I just thought I would post this as this looks like a very similar problem to mine on 64 bit Ubuntu.

---

### Post by kamina on 2010-05-31
Thanks for replies. I actually managed to get the normal flash to work by removing all the flash.so files under my home folder and /lib[64]/moz.../plugins. Then I just used software center to install the two flash options (till that point I had directly installled the alpha from adobe).

Now my problem would still be getting the debug player to work... Unless I manage I expect my boss will soon be pressuring me to use a different operating system (and I'm very close to getting this as our whole teams reference set up). 

Is there any 32bit stand alone browser that would allow the use of the same plugins? We could use that for the rare occasions when we need the debug player.

---

### Post by lovinglinux on 2010-05-31
> **Cavsfan said:**
> Don't mean to butt in **lovinglinux** as I am sure you know a lot more than I about all of this.

But, I had mentioned I was having problems with flash on youtube videos.
And I opened this thread _[http://ubuntuforums.org/showthread.php?t=1496785]("http://ubuntuforums.org/showthread.php?t=1496785%3Cbr%20/%3E")_

**Spr0k3t **posted a bug report and a workaround for the problem.
I was able to fix my problem just by doing step 3 of the workaround and everything works perfectly for me now.
I just thought I would post this as this looks like a very similar problem to mine on 64 bit Ubuntu.

The problem you was experiencing usually happens when you use a 32bit flash plugin with a 64bit browser. What my extension does is the Workaround 2, but it also removes conflicting plugins, which essential for those getting error messages about flash not being installed, even when it is installed.

I personally would recommend installing the 64bit flash version instead of using Workaround 3. But if that works for you, then great.

---

### Post by Cavsfan on 2010-05-31
> **lovinglinux said:**
> The problem you were experiencing usually happens when you use a 32bit flash plugin with a 64bit browser. What my extension does is the Workaround 2, but it also removes conflicting plugins, which essential for those getting error messages about flash not being installed, even when it is installed.

I personally would recommend installing the 64bit flash version instead of using Workaround 3. But if that works for you, then great.

I do have the 64 bit Java installed. I got it from the link in my sig. (A very good resource for updating Java)
On the right side it tells how to update 64 bit OS with 64 bit Java and the left side is for 32 bit OS and Java.

My Youtube videos worked fine, but I could never stop, pause, use CC, go to fullscreen or even be able to change the 
volume until I did step 3 of the workaround.

So this may be a different issue, but since 64 bit was mentioned, I thought it might be like my problem.

---

### Post by kamina on 2010-05-31
I did notice that play and pause did not work in youtube videos, but that does not really bother me so much. We have a flash based product and I need it to work (it does now). I just still need to figure out how I can also use the (32bit) debug player against it. :popcorn:

---

