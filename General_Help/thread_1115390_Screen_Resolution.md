---
title: "Screen Resolution"
date: 2009-04-03
forum: General Help
---

### Post by Briandb1222 on 2009-04-03
I have a Gateway 1.4 Ghz 512 MB RAM laptop. I put Ubuntu on it and it works just fine. However, the resolution is set at 1600 by 1200. Everytime I try to lower the resolution, my screen becomes scattered, messed up, real blurry, whatever you want to call it. Help Please. Is there a driver I need to install? I talked to a friend that has it. Suggested checking for updates, though I will still post this just in case.

---

### Post by Meson on 2009-04-03
Your refresh rate might be getting messed up.  That screen resolution utility doesn't work very well.  You might want to manually set things in /etc/X11/xorg.conf

---

### Post by Briandb1222 on 2009-04-03
What exactly would I change what to what?

---

### Post by Meson on 2009-04-03
That's a pretty loaded question, try reading "man xorg.conf"

It depends a little bit on your video card, maybe someone can post an example.

---

### Post by Briandb1222 on 2009-04-03
7th time I have reinstalled Ubuntu...reading the manual however I'm afraid that if I change it still won't work right. Is there another video driver I can install to help me out better?

---

### Post by Meson on 2009-04-03
> **Briandb1222 said:**
> 7th time I have reinstalled Ubuntu...reading the manual however I'm afraid that if I change it still won't work right. Is there another video driver I can install to help me out better?

You shouldn't need to reinstall because you don't like the way your screens are configured.

What video driver are you using now?  (The screen resolution settings should be independent of the driver, but nvidia for example, has some nice options to help you along.)

---

### Post by Briandb1222 on 2009-04-03
When I change the resolution it screws up the screen so bad I can't see what I am doing. Believe me if I could have avoided reinstalling Ubuntu 7 times, I would. I do not know how to look at system information to determine that.

---

### Post by Meson on 2009-04-03
You can boot up in recovery mode =)

---

### Post by soldats on 2009-04-04
> **Briandb1222 said:**
> I have a Gateway 1.4 Ghz 512 MB RAM laptop. I put Ubuntu on it and it works just fine. However, the resolution is set at 1600 by 1200. Everytime I try to lower the resolution, my screen becomes scattered, messed up, real blurry, whatever you want to call it. Help Please. Is there a driver I need to install? I talked to a friend that has it. Suggested checking for updates, though I will still post this just in case.

your refresh rates are probably wrong like the poster above said. go ahead and google what your monitor refresh rates are supposed to be and check to see if they are correct in your xorg.conf file located /etc/X11/xorg.conf
if they are wrong replace them with the correct ones and make sure you place the vertical and horizontal ones in the right place.

---

### Post by isaachan on 2009-04-04
> **Briandb1222 said:**
> 7th time I have reinstalled Ubuntu...reading the manual however I'm afraid that if I change it still won't work right. Is there another video driver I can install to help me out better?

Briandb, I have a similar machine (Gateway notebook made by emachines) got the same problem. Only resolution this laptop with ubuntu 8.10 is 1600x1200 so I can not see bottom and right side screen. I tried all other display options with no luck. Yea, I did same thing - reinstall everything from beginning. There is no other way because you can not see the screen! 

I learned shortcuts of Screen Resolution so I was able to go back. Screen
Resoltion has to go back the previous resolution if user has not confirm in 10 second or so. 

I tried ubuntu 9.04 beta. ubuntu 9.04 fixed the problem. If you messed up the screen resolution just wait few seconds resolution will reset. Nice. But it still same 1600 x 1200 only screen resolution.

I will keep looking this post. If I find a solution I will post here too.


Isaac

---

### Post by Briandb1222 on 2009-04-04
So, all I would have to do is go to 9.04 and my resolution problem would be fixed? If that is what you are saying I will try that. I have also talked to a computer repairsman. He said that maybe it is just my drivers not being up-to-date and that I should just update them. Though...being that Linux doesn't support most windows apps, it would be hard to do so unless I use Wine...which I was also having problems with.

---

