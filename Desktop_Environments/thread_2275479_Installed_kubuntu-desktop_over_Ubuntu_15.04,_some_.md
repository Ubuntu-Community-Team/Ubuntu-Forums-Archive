---
title: "Installed kubuntu-desktop over Ubuntu 15.04, some icons are missing."
date: 2015-04-26
forum: Desktop Environments
---

### Post by setittoubuntu on 2015-04-26
Hi,

I want to use dual desktop environment(Unity + KDE).

Today I've installed kde-desktop over my Ubuntu 15.04, and here is some annoying things that I encountered:

[http://imgur.com/QrTIuvW](http://imgur.com/QrTIuvW)
In first image category icons are missing.
[http://imgur.com/PQBi7Zb](http://imgur.com/PQBi7Zb)
In second image, some icons are missing like Shortcuts and Connectivity.

Now my question is, as obvious, how can I fix this? Is there a proper way of installing kubuntu-desktop over Ubuntu other than "sudo apt-get install kubuntu-desktop".

Thanks.

---

### Post by RobGoss on 2015-04-26
You can use the different [COLOR=#000000]desktop environments by installing them using your software manager as well as your terminal. After you've installed the desktop [/COLOR][COLOR=#000000]environments and want to switch from desktop to a different one, just log out then choose the desktop you want to use from the drop down menu and log back in. I hope this helps.[/COLOR]

---

### Post by setittoubuntu on 2015-04-26
Thanks but I doubt that you read my message.

I installed it over terminal, and ofc I logout and login with the respective DE, as you can see my screen shoots from KDE, not from Unity. Still some icons are missing, that's the problem.

---

### Post by RobGoss on 2015-04-26
> **setittoubuntu said:**
> Hi,

**I want to use dual desktop environment(Unity + KDE).**

Today I've installed kde-desktop over my Ubuntu 15.04, and here is some annoying things that I encountered:

[http://imgur.com/QrTIuvW](http://imgur.com/QrTIuvW)
In first image category icons are missing.
[http://imgur.com/PQBi7Zb](http://imgur.com/PQBi7Zb)
In second image, some icons are missing like Shortcuts and Connectivity.

Now my question is, as obvious, how can I fix this? Is there a proper way of installing kubuntu-desktop over Ubuntu other than "sudo apt-get install kubuntu-desktop".

Thanks.

As your post stated you want a dual boot **environment **my reply clearly indicated how to apply different  desktop &#8203;**environments. **As far as the missing icons maybe you did not install the desktop environment correctly.

---

### Post by cloestro on 2015-04-27
I have the same issue here.
But in my case I installed a fresh kubuntu 15.04 from scratch (official .iso files)

@robert: sorry but the original question was clear: no icons, how can I fix this?
As you can see on the screenshots, the user managed to log on kde (because these are kde screenshots).

---

### Post by setittoubuntu on 2015-04-27
So It's not an issue that happened because I installed it over Unity. 

I hope that I (or someone) could find a way, because I liked the new KDE, it's so smooth.

---

### Post by setittoubuntu on 2015-04-29
Anybody have a solution?(Sorry for "up", but still looking for an answer.)

---

### Post by QIII on 2015-04-29
You need not be sorry for bumping.  That's how this works.

If you don't get an answer this time, try bumping in 12 hours.  That will expose your thread to other people in different time zones.

---

### Post by tom185 on 2015-05-19
I have the same problem here. I was first on Kubuntu 15.04 and it was very nice, and then I installed the ubuntu-desktop package. After that, many icons were gone, fonts changed, and some more things (Only in KDE).
Then I reinstalled a fresh new Ubuntu 15.04 installation, and then installed the kubuntu-desktop package, and the problem persists.

---

### Post by it_self on 2015-05-25
Same issue here. Installed Kubuntu-desktop over Ubuntu 15.04 and have missing icons. I also have a few cliches in Chrome, but I think that may be unrelated. 
Do we have an answer yet on the icons? Has anyone just tried installed a new icon pack?

---

### Post by rafael_alcantara_perez on 2015-05-26
Same issue here. Is there any related bug registered in launchpad?

---

### Post by rafael_alcantara_perez on 2015-06-10
I've fixed the problem removing appmenu-qt5 (see [https://bugs.launchpad.net/appmenu-qt5/+bug/1434516](https://bugs.launchpad.net/appmenu-qt5/+bug/1434516)).

---

### Post by monkeybrain20122 on 2015-06-10
This is a bad idea anyway. Either use Ubuntu or Kubuntu.

---

### Post by tom185 on 2015-06-22
> **rafael_alcantara_perez said:**
> I've fixed the problem removing appmenu-qt5 (see [https://bugs.launchpad.net/appmenu-qt5/+bug/1434516](https://bugs.launchpad.net/appmenu-qt5/+bug/1434516)).

Wow, thank you so much!
Problem fixed now.

---

### Post by rafael_alcantara_perez on 2015-07-07
> **tom185 said:**
> Wow, thank you so much!
Problem fixed now.

You are welcome ;).

---

### Post by bamm750 on 2016-01-27
> **_alcantara_perez said:**
> I've fixed the problem removing appmenu-qt5 (see [https://bugs.launchpad.net/appmenu-qt5/+bug/1434516](https://bugs.launchpad.net/appmenu-qt5/+bug/1434516)).

Some seven month's since the last post; I know, it's an old topic. Except, I'm was (still am) using Kubuntu with Plasma when I decided to install Unity. That's when the multitude of problems crept up for me.

Finding the fix in this post, fixed the missing icons issue, but it also fixed an issue with dolphin icons. It also fixed a bunch of issues that I was having with themes, window decorations, and theme colors.

I suppose the bug lives on. Thanks for the fix, Rafael!

---

### Post by oldos2er on 2016-01-28
15.04 is going EOL in just a few days, so I'm closing this thread.

---

