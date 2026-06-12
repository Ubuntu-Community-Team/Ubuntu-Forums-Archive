---
title: "What Desktop is Ubuntu Studio?"
date: 2012-07-06
forum: Desktop Environments
---

### Post by hbnmgr on 2012-07-06
After upgrading to v11.10, I do not like my Desktop in Ubuntu Studio. Dont know what it is but someone suggested Unity Interface. How do I get Ubuntu Studio Desktop back or what Desktop Interface works with Studio? And how do I know I have Ubuntu Studio after this Upgrade???

---

### Post by LHammonds on 2012-07-06
[s]Newer versions of Ubuntu are using the interface called Unity[/s].  I saw a [post about how to change the 12.04 desktop into a classic view]("http://ubuntuforums.org/showthread.php?t=1966370") which may or may not help you out.

If you are just now upgrading (from something), why choose 11 when [12.04 is available]("http://ubuntustudio.org/download/")?

---

### Post by Frogs Hair on 2012-07-06
According to the documentation at the link , Ubuntu studio 11.10 comes with XFCE and not Unity.
[https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes](https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes)

Check your version:  [https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

---

### Post by hbnmgr on 2012-07-06
> **Frogs Hair said:**
> According to the documentation at the link , Ubuntu studio 11.10 comes with XFCE and not Unity.
[https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes](https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes)
 
Check your version: [https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)
 
Apparently, and according to the above mentioned page (release notes), the programmers are "transitioning to XFCE" and v11.10 suffered an "almost COMPLETE TEAM FAIL during this cycle". This could explain all the problems I've been having.
 
I will roll back to previous version and wait till the next LTS upgrade is available.
 
Thanks - and I hope I don't get punished for this post also.

---

### Post by Frogs Hair on 2012-07-06
You wrote nothing wrong in your post. Ubuntu Studio 12.04 LTS has been released and uses XFCE.  [http://cdimage.ubuntu.com/ubuntustudio/releases/precise/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/precise/release/)

---

### Post by hbnmgr on 2012-07-06
> **Frogs Hair said:**
> You wrote nothing wrong in your post. Ubuntu Studio 12.04 LTS has been released and uses XFCE. [http://cdimage.ubuntu.com/ubuntustudio/releases/precise/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/precise/release/)
 
Just noticed it was available ... Upgrading now!  But I hope I did not lose all my Email ?!?!?

---

### Post by Frogs Hair on 2012-07-06
> **hbnmgr said:**
> Just noticed it was available ... Upgrading now!  But I hope I did not lose all my Email ?!?!?

Thunderbird is default in Ubuntu 12.04.

---

### Post by hbnmgr on 2012-07-06
Upgraded to 12.04, but still have that funky Unity desktop. Ran the code in Terminal to install Xubuntu, but it came back "E: unable to locate package xubuntu-desktop".
 
I know where this is, it is trying to look for it on Disk. When I go to Software Sources there is nothing listed in the CD-Rom area. Also nothing checked under "Other Software" tab.
 
Help - How do I get rid of this desktop and get XFCE for Studio installed?

---

### Post by Frogs Hair on 2012-07-07
In the greeter box /login do you have more than one login option ?
In Ubuntu anyway when the icon next to the name is selected the different desktop environments are displayed.

When I view the Ubuntu Studio desktop in the 12.04 synaptic package manager it is described as XFCE . I have installed the Xubuntu desktop on 12.04 and it did not include Unity , but Studio may be different.

---

### Post by Frogs Hair on 2012-07-07
When you login are you sure you are seeing unity or the XFCE dock application as pictured in this review.   [http://cristalinux.blogspot.com/2012/05/ubuntu-studio-1204-review.html](http://cristalinux.blogspot.com/2012/05/ubuntu-studio-1204-review.html)

Try the following if so . This is from last year and may have changed . 

remove dock xfce
This is how you remove panel 2 which looks like a dock
1) right-click on the dock on the menu click panel preferences
2) there should be a box above the menus that says panel 2. click on the dash to delete panel 2 A.K.A the dock.
_

---

### Post by hbnmgr on 2012-07-07
> **Frogs Hair said:**
> In the greeter box /login do you have more than one login option ?
In Ubuntu anyway when the icon next to the name is selected the different desktop environments are displayed.
 
When I view the Ubuntu Studio desktop in the 12.04 synaptic package manager it is described as XFCE . I have installed the Xubuntu desktop on 12.04 and it did not include Unity , but Studio may be different.
 
Thanks!  The greeter box, after clicking that circle, shows these options ...
 
Recovery Console
Ubuntu
Ubuntu 2d
User Defined Session
XFCE session

---

### Post by hbnmgr on 2012-07-07
> **Frogs Hair said:**
> When you login are you sure you are seeing unity or the XFCE dock application as pictured in this review. [http://cristalinux.blogspot.com/2012/05/ubuntu-studio-1204-review.html](http://cristalinux.blogspot.com/2012/05/ubuntu-studio-1204-review.html)
 
Try the following if so . This is from last year and may have changed . 
 
remove dock xfce
This is how you remove panel 2 which looks like a dock
1) right-click on the dock on the menu click panel preferences
2) there should be a box above the menus that says panel 2. click on the dash to delete panel 2 A.K.A the dock.
_
 
Don't have that Panel.  The first icon on top is called "DASH Home". But clicked the DOT on the Greeter Box at Login and selected XFCE. Now this I am familiar with. 
 
Just don't know how to resolve the problem of using this Code;
```
sudo apt-get install ubuntustudio-desktop
```
and getting this response;
```
E: unable to locate package ubuntustudio-desktop
```
 
I found the above in another post, so there must be a Studio Desktop?!?!

---

### Post by Frogs Hair on 2012-07-07
Install the synaptic package manager if not already and look for it there. This is what appears in synaptic on my Ubuntu installation. If it is already installed which I think it might be you access the Ubuntu Studio applications from the XFCE session.

---

### Post by hbnmgr on 2012-07-07
> **Frogs Hair said:**
> Install the synaptic package manager if not already and look for it there. This is what appears in synaptic on my Ubuntu installation. If it is already installed which I think it might be you access the Ubuntu Studio applications from the XFCE session.
 
YES - That's what I needed/wanted. But Desktop does not show up in mine.
I went to Repositories, checked another option and then it showed up.
 
Installed it .... Now where do I find it so I can Activate it as my Desktop?

---

### Post by msammels on 2012-07-07
If you did install the Ubuntu Studio Desktop, all you need to do is log out, click the icon next to logon box and select "Ubuntu Studio".

---

### Post by kedarlasane on 2012-07-07
I think studio has more apps than desktop for a artist

---

### Post by msammels on 2012-07-07
It does. It has stuff like GIMP, music production, movie editing. I used to use it.

---

### Post by Frogs Hair on 2012-07-07
Check your version again.     [https://help.ubuntu.com/community/Ch...rUbuntuVersion](https://help.ubuntu.com/community/Ch...rUbuntuVersion)

---

### Post by hbnmgr on 2012-07-07
> **msammels said:**
> If you did install the Ubuntu Studio Desktop, all you need to do is log out, click the icon next to logon box and select "Ubuntu Studio".

That's just it ... it's NOT There ! ! ! 

Version Reports:
Ubuntu 12.04 LTS Precise

---

### Post by Frogs Hair on 2012-07-07
you must have installed XFCE and not Ubuntu Studio at some point. Does your desktop look Similar the one at the link and do you have the Studio applications displayed?   [http://cristalinux.blogspot.com/2012/05/ubuntu-studio-1204-review.html](http://cristalinux.blogspot.com/2012/05/ubuntu-studio-1204-review.html)

In your first post you said > After upgrading to v11.10, I do not like my Desktop in Ubuntu Studio. I am not sure how you got from Ubuntu Studio to Ubuntu 12.04. Are you sure you had Ubuntu Studio to begin with.

---

### Post by hbnmgr on 2012-07-07
> **Frogs Hair said:**
> you must have installed XFCE and not Ubuntu Studio at some point. 

YES - Apparently, but I simply selected it at Login.

> Does your desktop look Similar the one at the link and do you have the Studio applications displayed?   [http://cristalinux.blogspot.com/2012/05/ubuntu-studio-1204-review.html](http://cristalinux.blogspot.com/2012/05/ubuntu-studio-1204-review.html)

NO - it does not.

> I am not sure how you got from Ubuntu Studio to Ubuntu 12.04. Are you sure you had Ubuntu Studio to begin with.

Even Now as I am booting up it says Ubuntu Studio with an icon and a moving circle around it. Then the Login. I also noticed my Background will not show. I only have a black screen. Something must have gone wrong during Upgrade. I suspect that the upgrade to 12.04 took it from Ubuntu Studio to Ubuntu.

I have downloaded the Full version, burning it to DVD and will attempt a clean install. Just have to settle losing all info as the New Install will erase everything. Hope I can keep my dual boot as I have WinXP on another partition.

---

### Post by Frogs Hair on 2012-07-07
> **hbnmgr said:**
> YES - Apparently, but I simply selected it at Login.



NO - it does not.



Even Now as I am booting up it says Ubuntu Studio with an icon and a moving circle around it. Then the Login. I also noticed my Background will not show. I only have a black screen. Something must have gone wrong during Upgrade. I suspect that the upgrade to 12.04 took it from Ubuntu Studio to Ubuntu.

I have downloaded the Full version, burning it to DVD and will attempt a clean install. Just have to settle losing all info as the New Install will erase everything. Hope I can keep my dual boot as I have WinXP on another partition.

Reads like a good plan and if you have extra cds backup your data be fore installing. I'm not sure what happened in the course of the upgrades but something doesn't seem right. If you have problems with grub and XP after installing you can find help here 
just start a new thread if there are problems.

---

### Post by hbnmgr on 2012-07-09
Forget Upgrading to v12.04 from Live CD because of issue with PAE kernel requires from CPU - whatever that means. Would NOT Boot from NEW LIVE CD v12.04 UbuntuStudio.

Created new thread here;
[http://ubuntuforums.org/showthread.php?t=2021573](http://ubuntuforums.org/showthread.php?t=2021573)

I guess I we will just have to roll back to previous version and be stuck there until the programmers can figure this out. Apparently from now on they will require CPUs to have this PAE feature, else you are just out of luck ... meaning - NO UBUNTU FOR YOU!

Ending this Thread.
Nuff Said.

---

### Post by hbnmgr on 2012-07-11
Found the answer myself. Here is the Code;

```
sudo agt-get install ubuntustudio-desktop
```

Have bigger problems now, after upgrading to 12.04. All screwed up! Upgrade Failed.
Downloaded to Disk - install failed (posted elsewhere) due to CPU needs PAE capability.

Downloaded Mini ISO - install successful, but Pkgs and Updates FAIL.

Will start new threads with all the new problems.

Will this Ubuntu ever get right ???

---

### Post by Frogs Hair on 2012-07-11
If  you upgraded Ubuntu studio that command should not have been needed. If you added the Ubuntu studio desktop to Ubuntu and tried to upgrade , only the default Ubuntu would have been upgraded not the studio desktop . At least you have started with a new installation.

---

