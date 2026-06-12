---
title: "visual effects in ubuntu 11.04"
date: 2011-05-18
forum: Desktop Environments
---

### Post by arpit625 on 2011-05-18
I have recently installed ubuntu 11.04 in my computer.
In earlier versions of ubuntu there use to be a option of Visual effects in Appearence panel.
But when i open appearence in this new version there is no such option present there...
I have searched some other threads saying something related to "Compiz" .....saying visual appearence is related to that.....I was not able to find anything related to compiz in my os....i am not sure if they were correct .....

Can anybody tell from where to get visual effects option in ubuntu 11.04 ???

Thanks in advance......

---

### Post by garvinrick4 on 2011-05-18
Make sure this is installed here is screenshot of ccsm in ubuntu software center. click on screenshot.
When you need to open can hit windows key and A then type in ccsm and open.

---

### Post by SynonM on 2011-05-18
> **garvinrick4 said:**
> Make sure this is installed here is screenshot of ccsm in ubuntu software center. click on screenshot.
When you need to open can hit windows key and A then type in ccsm and open.


He's right!!! (search Ubuntu's Software Center for "Compiz". )

:popcorn:

Don't forget to add [solved].

---

### Post by mcduck on 2011-05-18
> **arpit625 said:**
> I have recently installed ubuntu 11.04 in my computer.
In earlier versions of ubuntu there use to be a option of Visual effects in Appearence panel.
But when i open appearence in this new version there is no such option present there...
I have searched some other threads saying something related to "Compiz" .....saying visual appearence is related to that.....I was not able to find anything related to compiz in my os....i am not sure if they were correct .....

Can anybody tell from where to get visual effects option in ubuntu 11.04 ???

Thanks in advance......

The visual effects are enabled by default (and can't be disabled while using Unity, which is why the option was removed from the Appearance dialog).

If you want to configure the effects, install CompizConfig Settings Manager.

---

### Post by cedneve on 2011-05-20
apt-get install compizconfig-settings-manager

Then System->Preferences->CompizConfig Settings Manager

There, you can disable all the plugins.

---

### Post by mcduck on 2011-05-20
> **cedneve said:**
> 
There, you can disable all the plugins.

What a nice way to get a broken desktop, by the way. Especially if you are using Unity... ;) Disabling all Compiz plugins while still using Compiz will only result in completely useless window manager, and in case of Unity also loosing all your panels.

If you want to get rid of the desktop effects, just select "Ubuntu Classic (No effects)" as your session from the login screen. Or install Unity 2D and use that as your session.

---

### Post by kyral210 on 2011-06-16
Wow this is bad! I upgraded and found I couldnt enable those lovely wobbly windows and other effects I loved to play with in 10.10. So I downloaded the app as said above and BOOM! I managed to break my deaktop. Now I have to find a way to get this back to how it was. Why didn't Ubuntu come with a very simple way to turn these things on and off without risking your desktop being screwed? I hate 11.04 right now, I really do. Not for one reason alone, but this one is one of them.

---

### Post by mcduck on 2011-06-16
> **kyral210 said:**
> Wow this is bad! I upgraded and found I couldnt enable those lovely wobbly windows and other effects I loved to play with in 10.10. So I downloaded the app as said above and BOOM! I managed to break my deaktop. Now I have to find a way to get this back to how it was. Why didn't Ubuntu come with a very simple way to turn these things on and off without risking your desktop being screwed? I hate 11.04 right now, I really do. Not for one reason alone, but this one is one of them.
Ubuntu *does* come with a very simple way to choose between using desktop effects and not using them. Just choose an appropriate session in the login screen.

It's techniacally impossible to provide such option when you are already running Unity, as Unity is a Compiz plugin so obviously it needs Compiz to work. Disabling desktop effects while running Unity would not work so providing an easy way to do that would be a bad idea.

Anyway, you can simply run "unity --reset" to automatically reload sane Compiz configuration that allows Unity to work (the command enables the Unity plugin and resets it's options to defaults, only touching other plugin's options if required to enable Unity plugin)

---

### Post by dhinteractive on 2011-06-16
lick on screenshot.
When you need to open can hit windows key and A then type in ccsm and open.

---

### Post by lalitha niharika on 2011-06-16
Hi!Even I am facing same problem.I installed compiz settings manager.But what should I do after that??plz explain me.I dont know anything about unity.Should I use classic?then what is the point in upgrading by wasting time?:(

---

### Post by mcduck on 2011-06-16
> **lalitha niharika said:**
> Hi!Even I am facing same problem.I installed compiz settings manager.But what should I do after that??plz explain me.I dont know anything about unity.Should I use classic?then what is the point in upgrading by wasting time?:(

What do you want to do? If you want to get rid of visual effects, then select the "Ubuntu Classic (No effects)" as your session in the login screen. (the option is in a dropdpown box  in the bottom panel of the login screen once you have selected an user but before you have input your password).

If you are trying to enable visual effects, there isn't anything you have to do. They are enabled by default.

---

### Post by Elline on 2011-06-16
> **lalitha niharika said:**
> Hi!Even I am facing same problem.I installed compiz settings manager.But what should I do after that??plz explain me.I dont know anything about unity.Should I use classic?then what is the point in upgrading by wasting time?:(

The point of upgrading is to have most recent packages (through current release is not very slick, I must admit).

If you want some certain effects, you need to go into compiz config settings manager and enable any plugins that you need (wobbly windows for example). They can possibly conflict with each other, so in this case you will be presented with a prompt, will you switch off conflicting plugin or leave it as is.

Should you use classic or unity is all upon your choice cause compiz will work in both cases and you always can have your effects.

If you need more reference about compiz, you can face here:[http://wiki.compiz.org/]("http://wiki.compiz.org/").

---

### Post by talhazelden on 2011-07-07
> **mcduck said:**
> If you want to get rid of the desktop effects, just select "Ubuntu Classic (No effects)" as your session from the login screen. Or install Unity 2D and use that as your session.

I thank you.

---

### Post by toumpas on 2011-07-08
> **mcduck said:**
> The visual effects are enabled by default (and can't be disabled while using Unity, which is why the option was removed from the Appearance dialog).

If you want to configure the effects, install CompizConfig Settings Manager.

Really huh?


I thought Compiz didnt work well with video playback and reduced performance alot. 

Btw i was looking about Compiz myself to give it a shot on a new netbook i bought.. Thanx to the 2nd post my question is answered.!

---

### Post by mcduck on 2011-07-08
> **toumpas said:**
> 
I thought Compiz didnt work well with video playback and reduced performance alot. 

That depends on your graphics card, and how good drivers you have for it.

With a correcty working graphics card using GPU acceleration for desktop, like you do with Compiz, will actually increase performance, offloading lots of the desktop drawing task to the GPU leaving your CPU more time to do things it's actually good for. And of course video playback works just fine as well, as long as your graphics card & drivers are up to the task.

If you have a very slow graphics card, or it's drivers don't include all the features required for running stuff like Compiz, it will have to use CPU instead for some of the work which will indeed slow your system down.

So, it's wrong to say Compiz would decrease your performance. It's supposed to do exactly the opposite, but depending on your setup things might not always work that well.

---

### Post by wildmanne39 on 2011-07-08
Hi, I have the cube and many effects and they work great in natty, I had to do a few adjustments to get it to work right but it does, here is a link for setting up the cube and effects with pictures for every step.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by jebasan on 2011-07-08
> **arpit625 said:**
> I have recently installed ubuntu 11.04 in my computer.
In earlier versions of ubuntu there use to be a option of Visual effects in Appearence panel.
But when i open appearence in this new version there is no such option present there...
I have searched some other threads saying something related to "Compiz" .....saying visual appearence is related to that.....I was not able to find anything related to compiz in my os....i am not sure if they were correct .....

Can anybody tell from where to get visual effects option in ubuntu 11.04 ???

Thanks in advance......

Hello to all Ubuntu users! I am not an advanced user as well, and i have just (2 days ago) updated my laptop from 9.10 to 11.4 and i think this is a matter of "getting used to it". yes, i had some problems at the beginning. On 9.10 I had the cube desktop, witch i love it, but right now I didn't have a chance to try on yet. And yes, i still have some problems with it also. But, once i have installed the 9.10 about 3 years ago and everything running the way i liked, i have never had ANY problem with my laptop. I have been through 3 years of school with it and all my classmates were stunned with my laptop. I have done all my school projects win it, even using qcad witch is a architecture software. Not a problem. So, be patient and go through the threads, there's answers to everybody.
Have a nice day to all.

---

### Post by Duncan Williams on 2011-07-08
The `Simple Compiz Config Settings Manager', or simple-ccsm.
Is the supposed utility that allows you to choose `desktop effects' 
in appearance.

If you want desktop effects and compiz (unity) with full control.
install:
> compiz
> compizConfig settings Manager (ccsm)
> fusion-icon (allows switch/set window managers and more)
> compiz-plugins-main
> compiz-gnome
> compiz-plugins-extra

from software manager or synaptic.

---

### Post by tnob on 2012-01-28
Hello everybody,

I also upgraded to 11.04 (from 10.04), just recently, and was slightly baffled (and also a bit miffed, I suppose) upon noting that my lovely rotating octagon & "jelly" windows had gone. The Compiz Fusion Icon icon is still there, though, but nothing happens when clicking on it.

And another thing: is it normal that, when upgrading, each and every step takes such a long time? Going from 10:04 to 10.10 and, subsequently, from 10.10 to 11.04 lasted practically a whole weekend!

tnob

---

