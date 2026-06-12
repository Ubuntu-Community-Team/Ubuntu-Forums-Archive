---
title: "Right-click on panel icons displays strange background pattern"
date: 2011-04-30
forum: Desktop Environments
---

### Post by spielball on 2011-04-30
There's a strange thing with the Gnome desktop. When I right-click on the trash icon or on icons in the panel, I get this:

[IMG]http://img714.imageshack.us/img714/1989/screenshotwz.png[/IMG]

[IMG]http://img62.imageshack.us/img62/434/screenshot1dj.png[/IMG]

How can I fix this?

---

### Post by spielball on 2011-05-01
I found out that this also happens when starting from live cd/stick. Perhaps I will remove v11.04 and switch down to 10.04. Natty Narwhale seems to be very buggy.

---

### Post by Krytarik on 2011-05-01
Does that issue occur with other themes as well?

---

### Post by spielball on 2011-05-01
Thank you for that hint. Why didn't I have that idea myself? :P

The problem only occurs with themes 'Ambiance' and 'Radiance'. All other themes do not show this problem. And of course, Ambiance and Radiance are basically the same theme except for the colors. So no wonder that they show the same problem.

I wonder if there are other users with the same problem. At the moment, I am on a fresh install of Natty Narwhale. So this is definitely a problem of those themes.

---

### Post by Krytarik on 2011-05-01
I just yet downloaded and tested both of those themes, and the issue didn't occur in my Lucid system. And I didn't notice that from other users so far.

Could you try creating a new user and logging in with those, to check if it's user specific?

---

### Post by spielball on 2011-05-01
I don't have that problem on Lucid either. I only have this since Natty. And I don't think it's user specific. Because I have this issue in any case. No matter if starting from live stick or using a permanent installation. As I said, I am on a fresh install, everything untouched.

However, I suspect it has to do with my graphics chip. I am one of those people with the intel chipset 855gm. I also have another problem. My mouse pointer disappears when I click on an icon or a menu item. This happens even though I log in with 'Classic (no effects)' desktop.

At the moment I am also looking for a solution for my graphics card. As of Natty, the problems should have been solved thanks to the new kernel. But still, I don't get any shadow or wobble effects. The tab 'Visual Effects' in System > Preferences > Appearance is not there when I login with the normal Classic desktop.

---

### Post by Krytarik on 2011-05-01
> **spielball said:**
> And I don't think it's user specific. Because I have this issue in any case. No matter if starting from live stick or using a permanent installation. As I said, I am on a fresh install, everything untouched.Ok, you said that about the liveUSB-stick before, sorry. Then it seems indeed related to a driver issue.
> **spielball said:**
> 
The tab 'Visual Effects' in System > Preferences > Appearance is not there when I login with the normal Classic desktop.
There is such option tab anymore, those features are now handled by the session settings itself.

But you can log in to "Ubuntu" (thus Unity) and have the launcher/panel?

---

### Post by spielball on 2011-05-01
No, I can't login with Unity. My graphics card is too weak and thus not supported. I can only login to 'Ubuntu classic'. Still, I try to figure out how to get the normal desktop with shadows under menus and windows. Because for v10.04 there was a fix provided from here:

[http://www.glasen-hardt.de/?page_id=707](http://www.glasen-hardt.de/?page_id=707)

On this blog, it's also said that with the new kernel of 11.04, the graphics card problems of the 855gm should be fixed. It works, but still I don't have shadows and also my mouse pointer disappears when I click an icon or menu item or rest it after moving. I searched the forum, but couldn't find a solution. First I thought it has to do with 'unclutter'. But this is not installed on my system.

Now I try to figure out what I have to do. I fiddled around with xorg.conf as described on the mentioned blog. But I ended up with a black screen then.

EDIT:
I'm not sure if this is only because of the graphics card. Other themes  don't have this issue. I also installed the newest drivers for the intel  card. No matter if I enable the intel drivers or keep using the  framebuffer - this bug is always there and affects those menus when  in 'no effects' mode.

---

### Post by RossWindows on 2011-05-06
I'm also experiencing the issue with the odd background pattern. This is a fresh Natty install except for having installed the proprietary Nvidia drivers.
It happens when I right-click on the trash icon or the "show the desktop" icon, and it happens when I right click on the four-square workspaces area in the lower right-hand corner of my screen.

It does not appear when I right-click on an empty space of the lower toolbar, or on the task bar area of an open application, i.e. I have Chromium open right now and therefore I have an icon in the lower left of my screen for the open application and when I right-click on that, it has a normal background.

I'm using an Nvidia graphics card and drivers with the following model/version
Graphics Processor: GeForce 9600 GT
NVIDIA Driver Version: 270.41.06

Hope that helps!

---

### Post by 3ldi5 on 2011-05-29
+ 1 here.

I encountered the same bug yesterday, on fresh Natty install, after 5 minutes of use, and I was pissed of, because I hate those visual-related bug mostly, especially if they occur out of the box.
So I uninstalled it immediately, and decided to try Mint 11, just to find out that the same bug is appearing in Mint too.

So I don't know is it something to Ambiance/radiance theme or not, but it's annoying. In Mint's default theme Mint X Metal, the same thing is happening.

I don't believe that this is something to do with graphic cards. I never had any problems with Lucid or Maverick, and I'm using ancient Radeon 9600 pro. This is some weird bug in Natty.

Heh, like they decided, ok, all of you who don't like our amazing Unity thing, we will pack you a buggy Gnome panels. :)

Edit. Well, like I said, this is a bug [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/711746](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/711746), reported and solved already.

---

