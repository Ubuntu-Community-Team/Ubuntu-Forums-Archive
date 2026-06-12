---
title: "How Stable and Polished is Xubuntu?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by blacknyx on 2006-06-30
I've been using ubuntu for quite some time now and I LOVE it.
But I really love fvwm, fluxbox, and openbox as my GUI desktop over Gnome.

So I was thinking perhaps I could benefit from using Xubuntu instead of Ubuntu.  
But I was wondering.  

Is it pretty well kept up right now?  Does anybody know?
How stable is it?
Can I get all of the same packages from Dapper?

If I already have fvwm running on my Ubuntu, is it worth it to reinstall with Xubuntu?

Thanks guys.  Sorry if this is in the wrong forum.  I wasn't real sure where to put it.

---

### Post by dermotti on 2006-06-30
I think Xubuntu is VERY stable and VERY polished. 

Yes you can get all the same programs.

---

### Post by IYY on 2006-06-30
I don't think there is a need to re-install. Xubuntu is pretty much just Ubuntu with XFCE (but yes, this also means that you have the exact same repositories).

---

### Post by blacknyx on 2006-06-30
Good to know.  Maybe I'll do it just to entertain myself this weekend.  Yes I'm weird, this is my way of entertaining myself, installing new distros of linux far too often.
dermotti, thanks for the link in your sig, I'm reading up on the updates now.  Looks good to me!

---

### Post by missmoondog on 2006-06-30
simply install xubuntu desktop and then change sessions. everything works great together. if you learn to like xubuntu! i didn't learn. :(
mainly wanted to try xfce to use on this old HP. didn't make squat for a difference.

---

### Post by msandersen on 2006-06-30
If you already have Ubuntu, you don't need to reinstall. Open the Terminal and type
```
apt-get install xubuntu-desktop
```
and everything in the Xubuntu ditribution will be installed. If you have a Xubuntu CD, set it as a source first in Synaptic or in the Terminal
```
apt-cdrom add
```
You prob need to Update to get CD package list recognised.
Then reboot and choose your window manager of choice.

---

### Post by Wr8EYilK8Y on 2006-06-30
What is the difference between Gnome and XFCE? I want to know. I have Xubuntu CDs but don't know if there is a real difference.

---

### Post by msandersen on 2006-07-01
I've never used it; but it's basically a lighter and supposedly faster window manager, whereas Gnome is a full Desktop Environment, although they're both based on GTK+. The current release has an inbuilt composition manager. Gnome 2.16 will as well. So basically, if you have older hardware, or just want a smaller faster window manager, it may be for you. Or if you simply like it.
But if you have the LiveCD, you should be able to tell the look-and-feel differences youself.
[http://en.wikipedia.org/wiki/Xfce](http://en.wikipedia.org/wiki/Xfce)
[http://www.xfce.org/](http://www.xfce.org/)

---

### Post by MetalMusicAddict on 2006-07-01
I really reccommend Xubuntu for the intermediate/experienced Ubuntu user. There are less apps to config with a GUI so lots of things are done manually. The Dapper release is 10 fold better than the last polish-wise. I use it on my server and for gaming. See my thread [HERE]("http://www.ubuntuforums.org/showthread.php?t=199092").

Screenshot:
[[IMG]http://img261.imageshack.us/img261/6626/new1yb.th.png[/IMG]](http://img261.imageshack.us/img261/6626/new1yb.png)
No panels just icons. The menus are accesed on right and middle-clicks.

I am thinking to use it as my full-time desktop though.

---

### Post by aysiu on 2006-07-01
[QUOTE=msandersen]If you already have Ubuntu, you don't need to reinstall. Open the Terminal and type
```
apt-get install xubuntu-desktop
```
and everything in the Xubuntu ditribution will be installed. If you have a Xubuntu CD, set it as a source first in Synaptic or in the Terminal[/quote] I would highly recommend against installing *xubuntu-desktop* with Synaptic or *apt-get*, as you will then find *xubuntu-desktop* more difficult to remove later. ```
sudo apt-get remove xubuntu-desktop
``` will do essentially nothing.

Use *aptitude* instead: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
``` Read more here about why: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

>  ```
apt-cdrom add
```
You prob need to Update to get CD package list recognised.
Then reboot and choose your window manager of choice. Don't forget that the CD must be the Alternate CD. You cannot install Xubuntu from the Desktop CD.

---

### Post by msandersen on 2006-07-02
Here's hoping they fix apt-get and Synaptic by the next release, then, considering they are the standard. I've tried gkorphan, it suggests all sort of libraries which are needed by other applications. Hardly orphans.

---

### Post by aysiu on 2006-07-02
*apt-get* need not be the standard. I always advise people to use *aptitude*.

---

### Post by The Land of Smeg on 2006-07-02
I find Xubuntu/Xfce to be pretty polished, but not as well polished as Ubuntu/Gnome. Although they look simular, I found that the Panel items available arn't as good quality as Gnome's and I found myself having to go into terminal and CHMODing the menu.xml to 777 so that I could edit it. It's minor things like that which leaves room for improvement because as powerful as terminal is, it shouldn't need to be used in a user friendly distribution.

---

