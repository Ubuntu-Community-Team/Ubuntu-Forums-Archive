---
title: "Add support for tear-free compositing in Xfce"
date: 2014-03-21
forum: Desktop Environments
---

### Post by tamir2 on 2014-03-21
This is the dilemma
Video  in motion scenes with stripes. When installing composite window Manager  (compiz) everything is fine. The problem is, since Ubuntu 12.04 x64  (xfce) or x86 (xfce) to Ubuntu 14.04. Created a bug report, can someone  have something constructive or have any additional information please  post.
 Link to the bug report -[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/1294600.]("https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/1294600")

---

### Post by Toz on 2014-03-21
Hello and welcome to the forums.

Have you tried Compton (see [here]("http://ubuntuforums.org/showthread.php?t=2144468")) for more information. Also, in 14.04, an option to synchronize the vertical blank has been added. Not sure how effective it is since I don't have a tearing problem to test it on.

---

### Post by tamir2 on 2014-03-21
[**[COLOR=#C61919][B]Toz**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=27546"), 
thanks for the response, I will check Compton, besides I want to check on Xubuntu 14.04 on your device, but don `t know that it is better to download the daily builds or beta where to download it.

---

### Post by ajgreeny on 2014-03-21
Compton is in the universe repos of trusty, so you can try it easily.

The configuration of compton is more detailed than many other composite managers, but the example shown in the linked post works well in my 12.04 install of Xubuntu, and I have no problems in 14.04 in a VM to have bothered with trying it; a VM may negate any answers I get from using it anyway.

PS: You can get the daily builds from [http://cdimage.ubuntu.com/xubuntu/daily-live/pending/](http://cdimage.ubuntu.com/xubuntu/daily-live/pending/) which is probably better than the beta image as many updates have arrived since beta.

---

### Post by tamir2 on 2014-03-21
[**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747") 

In repos of saucy it is not, installed according to the instructions given to me, checked tearing problems remained. And in Xubuntu 14.04 like Compton is not needed. Already downloading daily build (thanks for the link) and there will test)).

---

### Post by ajgreeny on 2014-03-21
> **tamir2 said:**
> [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747") 

In repos of saucy it is not, installed according to the instructions given to me, checked tearing problems remained. And in Xubuntu 14.04 like Compton is not needed. Already downloading daily build (thanks for the link) and there will test)).

Sorry, I thought you were already using trusty from what you said in your first post.

---

### Post by tamir2 on 2014-03-21
[B]ajgreeny
[/B]nothing terrible bug was created in Xubuntu 13.10 (link in first post).
Installed  Xubuntu 14.04. How to enable vertical blank? By default, all as Xubuntu  13.10(((. Have to install Compton , for trusty this instructions will  apply ([http://ubuntuforums.org/showthread.php?t=2144468](http://ubuntuforums.org/showthread.php?t=2144468))?

---

### Post by ajgreeny on 2014-03-21
Sorry, I never used 13.10 so was not aware of that and I did not have any problems with tearing on 12.04, even though I do use compton on my installation.

You do,not need to do anything special to get compton in trusty as it is in the repos and available in the normal way with apt-get or software-centre.

I use the config file in my 12.04, exactly as it is in that linked post, but I have an intel HD4000 graphics system; your situation my be different.

---

### Post by tamir2 on 2014-03-22
Installed Compton from the Software Center, but do not know how to run it. On the laptop AMD A6-4400m+AMD 7670m dual graphics from AMD.
Can someone tell me how to do it on Xubuntu 14.04 trusty?

---

### Post by ajgreeny on 2014-03-22
Create your hidden **.compton.conf** file in home (I used the one in that linked post) and then add compton with command **compton -b** to the list in **Settings-Manager ->Session & Startup ->Application Autostart** tab.

Make sure that compositing is not also set in the Window Manager Tweaks of Settings-manager.

---

### Post by tamir2 on 2014-03-22
[**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")
thanks for the help, but this method does not want to work on my laptop).
Okay, **Toz **and **ajgreeny** thanks for the response. And you answered that there is no change in Xfwm4 will never be done - [https://bugzilla.xfce.org/show_bug.cgi?id=10407](https://bugzilla.xfce.org/show_bug.cgi?id=10407)

---

### Post by Yellow Pasque on 2014-03-22
> but this method does not want to work on my laptop
Be more specific. Does compton not start? Does it run okay, but still cause tearing?

---

### Post by Sunbriel on 2014-08-01
Hate to bring the thread back from the dead, but same problem here. Comtpon simply does nothing on my laptop even though it's running. On my PC it works fine (with some minor bugs), but on both Asus K95VJ and Asus K53SV, it doesn't work. It is worth mentioning that both laptops have hybrid graphics (nvidia and intel) - with nvidia there's always screen tearing, but with intel there is no screen tearing even without Compton (this is the case with other DEs, not sure if it applies to XFCE as well, as I've tried  a lot of distros in a short period of time). This has been a never ending search for tear-free Linux distro for my laptop.

---

