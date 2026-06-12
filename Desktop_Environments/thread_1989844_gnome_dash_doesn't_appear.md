---
title: "gnome dash doesn't appear"
date: 2012-05-28
forum: Desktop Environments
---

### Post by Djesurun1 on 2012-05-28
Hello there Ubuntu fans! I'm still very new to Ubuntu (and Linux) but I'm learning. I just built a computer and here are the specs that might be applicable: ASUS Motherboard, AMD Phenom II X4 processor, NVIDIA Geforce 210 graphics card, Ubuntu 12.04. I'm running dual monitors and I just installed GNOME from the software center. For some reason the activator hotspot doesnt open my dashboard. I've looked through the forums and the interwebs but all I seem to find are topics on how to remove the dashboard lol. I've never seen the dash so I'm not sure if maybe I have a conflict with my graphics card or what. It makes me wonder if I ever even had unity 3d before installing gnome. I've tried removing my graphics card and using the on board video card but it didn't function any different. I log in and its the same situation. Also, I've noticed on videos and pictures of GNOME that the menus at the top say "activities" but mine says "applications". I've included a pic of my desktop...its much more basic than the pictures that I've seen...i want all the cool flare lol. In the picture my mouse is on the top left corner, as you can see it just displays the message "browse and run installed applications". On the login i did select GNOME not GNOME CLASSIC. Any help would be much much much appreciated. Thanks!

---

### Post by Djesurun1 on 2012-06-02
Hmm Im guessing this isn't a common problem from the lack of responses lol. Is anyone at all knowledgeable about what this could be? Thanks again!

---

### Post by traditionalist on 2012-06-02
> **Djesurun1 said:**
> Hmm Im guessing this isn't a common problem from the lack of responses lol. Is anyone at all knowledgeable about what this could be? Thanks again!

What happens when you <Left Mouse Click> on "Applications" ?  Don't you get a drop down menu?  Like this;

[[IMG]http://img841.imageshack.us/img841/1732/workspace1001j.th.png[/IMG]](http://img841.imageshack.us/i/workspace1001j.png/)

---

### Post by Djesurun1 on 2012-06-02
yes I do have something similar when i click applications i get: 

Accessories
Games 
Graphics
Internet
Office   etc...

Isn't there supposed to be a hotspot that activates a dashboard in that corner though? 
I was under the impression it would look something like this with a dashboard...

---

### Post by traditionalist on 2012-06-02
> **Djesurun1 said:**
> yes I do have something similar when i click applications i get: 

Accessories
Games 
Graphics
Internet
Office   etc...

Isn't there supposed to be a hotspot that activates a dashboard in that corner though? 
I was under the impression it would look something like this with a dashboard...

What happens on various systems depends on what you have installed, and what you choose when you log in.  You apparently have Gnome running.  That is normal behaviour for Gnome.

At your log in panel, click on the image in the upper right corner of the panel and see what else you can choose.

If you want a dashboard for Gnome, you can install one ;

[http://www.omgubuntu.co.uk/2012/05/unity-dash-like-gnome-shell-extension-sees-release](http://www.omgubuntu.co.uk/2012/05/unity-dash-like-gnome-shell-extension-sees-release)

Unfortunately the terminology for all this stuff can be extremely confusing. It takes a while until you know what is what and what it actually does.

---

### Post by Djesurun1 on 2012-06-02
Yeah, unfortunately I'm lost in all of this terminology lol. I've clicked on the cog at the login and tried all of the different options from gnome to gnome classic and several others but I still dont see that dash that ive seen in all of the reviews or images of gnome. Specifically in all of the youtube videos or reviews ive seen of the newer version of gnome, right after install i "should" have a hotspot on the corner (where it says applications) and when my mouse hovers over that corner it should activate a dashboard with common apps. I'm just not sure why mine is so basic and the dash is nonexistent. I even installed a dash called "pie" and it never opens, functions, or seems to exist. I've since uninstalled it. I can get to the apps i need but im curious why mine doesn't seem to function properly.

---

### Post by traditionalist on 2012-06-02
> **Djesurun1 said:**
> Yeah, unfortunately I'm lost in all of this terminology lol. I've clicked on the cog at the login and tried all of the different options from gnome to gnome classic and several others but I still dont see that dash that ive seen in all of the reviews or images of gnome. Specifically in all of the youtube videos or reviews ive seen of the newer version of gnome, right after install i "should" have a hotspot on the corner (where it says applications) and when my mouse hovers over that corner it should activate a dashboard with common apps. I'm just not sure why mine is so basic and the dash is nonexistent. I even installed a dash called "pie" and it never opens, functions, or seems to exist. I've since uninstalled it. I can get to the apps i need but im curious why mine doesn't seem to function properly.

The dash is really a "unity" thing, and I don't know very much about it at all. It is possible that your machine is starting in "fallback" mode because it is unable to support unity. But that's just a guess on my part.

There will be somebody along who knows exactly what is going on and can explain it to you.

---

### Post by Djesurun1 on 2012-06-02
Hmm i had seen something about a fallback mode. I'll look into that more! I hope someone can help me figure out whats going on with my computer. Thanks for your time!

---

### Post by Djesurun1 on 2012-06-03
Ok so i have narrowed my problem down to my graphics card. It is a Nvidia PNY GeForce 210 512mb video card. When I go to system details and click graphics it says:

Driver - unknown
Experience - Fallback

I checked in my system settings and under additional drivers I have:

Nvidia accelerated graphics driver (current version) [Recommended]
Nvidia accelerated graphics driver (post release updates) version current updates

I have activated each one separately, restarted, and still the same problem. Could the problem be that my on board graphics card is causing an issue? I have no idea how to check but I am using my nvidia card for dual monitors and everything works fine except the 3d unity and gnome shell.

---

### Post by Djesurun1 on 2012-06-10
Ok so I am still really quite stuck here. I don't know what i did wrong but why doesn't gnome look like it should? I'm really losing my mind trying to figure this out. Ive installed and checked these drivers countless times. Please...anyone who is familiar with this problem help! I just spent a lot of money getting this computer to work again...i would love it if ubuntu was working properly =/

---

### Post by Djesurun1 on 2012-06-23
Time to mark this as solved! I finally found a solution. I came across a program called compiz-check and it basically checks for any hardware issues. Well it found two and they were both solved by opening the .XORG file and editing the line that says Composite = "Disabled" to Compisite = "Enabled". Like magic i changed that saved the file Gnome looks exactly  like it should with all the eye candy, bells and whistles. Woohoo! I really hope this can help someone else cuz that was frustrating.

---

