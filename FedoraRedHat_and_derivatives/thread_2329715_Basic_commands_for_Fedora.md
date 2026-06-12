---
title: "Basic commands for Fedora"
date: 2016-07-04
forum: Fedora/RedHat and derivatives
---

### Post by RobGoss on 2016-07-04
I was wondering about Fedora do they use different command then Ubuntu and Linux mint?

I want to know the basics like installing updates and software application. Is Fedora that much different then Ubuntu?

I was reading some were that Fedora uses the **Yum** command with Fedora appose to **Sudo **in Ubuntu, is this correct

Thanks so much

---

### Post by QDR06VV9 on 2016-07-04
Most commands are the same across Linux Distros, But some differences are worth noting:
See This:[http://fedoralinuxcommands.blogspot.com/](http://fedoralinuxcommands.blogspot.com/)

---

### Post by RobGoss on 2016-07-04
Nice reference sheet thanks, but is there a **superuser **needed like we use with **Ubuntu, sudo** needed to run certain commands like install updates?

---

### Post by QDR06VV9 on 2016-07-04
> **RobGoss said:**
> Nice reference sheet thanks, but is there a **superuser **needed like we use with **Ubuntu, sudo** needed to run certain commands like install updates?

Yes!
So, to get root access: a user uses sudo to run a program as root. 
And this was left out of the link I sent you
```
su 
```
Method to go root.
[COLOR=#ff0000][U][B]And This is just meant to be an example only

[/B][/U][/COLOR]_**[COLOR=#ff0000][/COLOR]**_To upgrade to a newer  Release
```
Fedora 23 -> Fedora 24

# rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-fedora-24-$(uname -i)
# dnf upgrade
# dnf clean all
# dnf --releasever=24 --setopt=deltarpm=false distro-sync


```
So each new Linux OS you run there are enough differences to read about them to save yourself frustrations.
And may I add that this is not a Noob friendly OS
As Quoted from Distro Watch
> This isn't its reputation, however -- at least, not completely. In the  forums, users write that they like it because it's a cutting edge distro  with the most up to date software and with a commitment to software  freedom, certainly not a distro for newbies, but great for those who  want to be on the cutting edge. 

Source:[http://distrowatch.com/weekly.php?issue=20160704#fedora](http://distrowatch.com/weekly.php?issue=20160704#fedora)

---

### Post by QIII on 2016-07-04
Moved to Fedora/RedHat and derivatives.

---

### Post by QDR06VV9 on 2016-07-04
> **QIII said:**
> Moved to Fedora/RedHat and derivatives.

You Just beat me:P to the move.

---

### Post by Dennis N on 2016-07-04
If you want a user friendly remix of Fedora, use Korora. Almost everything is set up ready to go out of the box. I have been using Korora 23 XFCE.

---

### Post by RobGoss on 2016-07-04
> **Dennis N said:**
> If you want a user friendly remix of Fedora, use Korora. Almost everything is set up ready to go out of the box. I have been using Korora 23 XFCE.


Hello Dennise, is it more user friendly the Fedora 24? 

I think I found it I will give it a try also [https://kororaproject.org/](https://kororaproject.org/)

Thanks so much

---

### Post by Dennis N on 2016-07-04
Korora 24 is not released yet. I understand it will take a few weeks after release of Fedora 24 (which was just released) before it is out. Korora 23 (current version) is supported until Fedora 25 is released about 6 months from now.

---

### Post by RobGoss on 2016-07-04
> **Dennis N said:**
> Korora 24 is not released yet. I understand it will take a few weeks after release of Fedora 24 (which was just released) before it is out. Korora 23 (current version) is supported until Fedora 25 is released about 6 months from now.

Yes I'm downloading it now to see how it looks, thanks for letting me know about it. Have a safe 4th July my friend

---

### Post by Dennis N on 2016-07-04
I hope you enjoy it. I am of the school that it is a good idea to have some familiarity with some non-Debian systems. Widen your world. A good holiday to you too.

---

### Post by RobGoss on 2016-07-04
I like it so far just installed it on a USB and ran a live session seems very clean and responsive. I will try installing it a just a few :)

---

### Post by QIII on 2016-07-05
> **RobGoss said:**
> Have a safe 4th July my friend

Please realize that most people here, not being from the US, don't really care about US Federal Holidays and celebrations -- and may find mention of such either political in nature, ugly-Americanisms, or just plain irritating.

Thanks.

---

### Post by buzzingrobot on 2016-07-05
> **RobGoss said:**
> 
I want to know the basics like installing updates and software application. Is Fedora that much different then Ubuntu?

I was reading some were that Fedora uses the **Yum** command with Fedora appose to **Sudo **in Ubuntu, is this correct



Fedora uses a different package manager and a different dependency resolver than Ubuntu, Mint or other distribution in the Debian lineage.

Packages in Fedora are created in the .rpm format, while Ubuntu packages are created in the .deb format.

Fedora use the "rpm" command to deal with packages at an individual level.  Ubuntu uses "dpkg",

Fedora uses "dnf" where Ubuntu use apt/apt-get.  (dnf was introduced a few releases ago to replace yum, which was very old and, apparently, difficult to maintain.)

The capabilities of both systems are equal, but, of course, different tools means things are sometimes done in different ways.

The primary Fedora release is based on Gnome, and new Fedora releases inevitably role out with the most recent Gnome version. KDE, MATE, XFCE, Cinnamon, and LXDE spins are also offered, Fedora releases every 6 months or so (releases are delayed for bug fixes, etc.)   A release has a support lifetime of just about 13 months (it's not fixed in stone) so *two* releases are supported simultaneously.

Fedora does not ship, or host in its repos,  non-free packages, such as codecs and proprietary video drivers.  These are available elsewhere.  But, users are on their own to cope with breakage, especially with video drivers, when something like a kernel update comes along.

---

### Post by RobGoss on 2016-07-05
> **buzzingrobot said:**
> Fedora uses a different package manager and a different dependency resolver than Ubuntu, Mint or other distribution in the Debian lineage.

Packages in Fedora are created in the .rpm format, while Ubuntu packages are created in the .deb format.

Fedora use the "rpm" command to deal with packages at an individual level.  Ubuntu uses "dpkg",

Fedora uses "dnf" where Ubuntu use apt/apt-get.  (dnf was introduced a few releases ago to replace yum, which was very old and, apparently, difficult to maintain.)

The capabilities of both systems are equal, but, of course, different tools means things are sometimes done in different ways.

The primary Fedora release is based on Gnome, and new Fedora releases inevitably role out with the most recent Gnome version. KDE, MATE, XFCE, Cinnamon, and LXDE spins are also offered, Fedora releases every 6 months or so (releases are delayed for bug fixes, etc.)   A release has a support lifetime of just about 13 months (it's not fixed in stone) so *two* releases are supported simultaneously.

Fedora does not ship, or host in its repos,  non-free packages, such as codecs and proprietary video drivers.  These are available elsewhere.  But, users are on their own to cope with breakage, especially with video drivers, when something like a kernel update comes along.

Thanks** Buzzingrobot**, This is great information to know I would like to learn the different usage of command for other distributions also

---

### Post by Dennis N on 2016-07-07
Most of the differences are in the package management commands. Other bash commands are mostly the same. Fedora/Korora sets up root password but also has sudo. First time with Fedora installer I didn't notice "Make this User administrator" box - so no administrator tasks were allowed for my user, such as installing software or anything requiring sudo in Ubuntu. What to do? Since there was a root password created, I was able to use it to make my regular user an administrator and get on with it.

I first did Fedora 22 as a learning tool, but after finding Korora 23, switched over.

A good read for starters:

[http://www.zdnet.com/article/korora-23-coral-hands-on-with-all-five-desktop-versions/](http://www.zdnet.com/article/korora-23-coral-hands-on-with-all-five-desktop-versions/)

---

### Post by RobGoss on 2016-07-07
> **Dennis N said:**
> Most of the differences are in the package management commands. Other bash commands are mostly the same. Fedora/Korora sets up root password but also has sudo. First time with Fedora installer I didn't notice "Make this User administrator" box - so no administrator tasks were allowed for my user, such as installing software or anything requiring sudo in Ubuntu. What to do? Since there was a root password created, I was able to use it to make my regular user an administrator and get on with it.

I first did Fedora 22 as a learning tool, but after finding Korora 23, switched over.

A good read for starters:

[http://www.zdnet.com/article/korora-23-coral-hands-on-with-all-five-desktop-versions/](http://www.zdnet.com/article/korora-23-coral-hands-on-with-all-five-desktop-versions/)


Hi Dennis, Yea I'm having trouble with Fedora now trying to **install software** and run simple commands from the command line like just doing a simple system update, Ubuntu sure does make it easire for it's users

I've added the other user and added the wheel thing but no luck yet, they take about having to login out and all and I think this is just a waist of time having to do this just to get things working as they should

---

### Post by QIII on 2016-07-07
I'm not sure why yum -- now dnf -- is any more difficult than aptitude or apt-get.

Not sure how the graphical method is any more difficult, either.

---

### Post by RobGoss on 2016-07-07
> **QIII said:**
> I'm not sure why yum -- now dnf -- is any more difficult than aptitude or apt-get.

Not sure how the graphical method is any more difficult, either.

It seems that **yum** in some cases is not used anymore which I believe **dnf **has replaced it. Fedora won't run like Ubuntu right out of the box

A lot of standard software that comes with Ubuntu does not come with fedora so you have a manually install it which they don't make it any easier for users

I have a old dell latitude I installed it on just to see what was so different about it

---

### Post by Dennis N on 2016-07-08
> **RobGoss said:**
> It seems that **yum** in some cases is not used anymore which I believe **dnf **has replaced it. Fedora won't run like Ubuntu right out of the box. A lot of standard software that comes with Ubuntu does not come with fedora so you have a manually install it which they don't make it any easier for users

All true. That's why Korora was created! 

I don't know what Desktop you chose, but I have Korora XFCE since I prefer Xubuntu working in the Ubuntu family.

A couple of comments that come to mind:

There is no equivalent to Ubuntu's "Software Center" or Ubuntu MATE's "Software Boutique". So you have to know what the main Linux packages for various purposes are called. To get some software, I had to install the RPM Fusion Repository in Fedora - for a newbie at Fedora, that takes some searching on how to do. In contrast, with Korora, RPM Fusion is already installed and ready to use. Flash player is in the adobe repository - In Korora, you need to enable the repository in Yumex (Yum Extender) preferences > repositories. In Fedora, you may have to install the repository as well. Yumex is good for installing - something like Synaptic Package Manager. Of course, you can use the terminal as well if you know the name: **sudo dnf install package**

Documentation: [http://yumex-dnf.readthedocs.io/en/latest/](http://yumex-dnf.readthedocs.io/en/latest/)

---

### Post by RobGoss on 2016-07-08
> **Dennis N said:**
> All true. That's why Korora was created! 

I don't know what Desktop you chose, but I have Korora XFCE since I prefer Xubuntu working in the Ubuntu family.

A couple of comments that come to mind:

There is no equivalent to Ubuntu's "Software Center" or Ubuntu MATE's "Software Boutique". So you have to know what the main Linux packages for various purposes are called. To get some software, I had to install the RPM Fusion Repository in Fedora - for a newbie at Fedora, that takes some searching on how to do. In contrast, with Korora, RPM Fusion is already installed and ready to use. Flash player is in the adobe repository - In Korora, you need to enable the repository in Yumex (Yum Extender) preferences > repositories. In Fedora, you may have to install the repository as well. Yumex is good for installing - something like Synaptic Package Manager. Of course, you can use the terminal as well if you know the name: **sudo dnf install package**

Documentation: [http://yumex-dnf.readthedocs.io/en/latest/](http://yumex-dnf.readthedocs.io/en/latest/)

Korora sounds good I have it also loaded up on a USB and have tested it also. I might just go with Korora instead of Fedora.

I think Fedora needs to work on making things available like other distributionside do and maybe more people would use I

Thanks so much for the tips Dennis

---

### Post by Dennis N on 2016-07-08
When I said "for a newbie at Fedora, that takes some searching on how to do" I was referring to myself. I did a lot of googling for answers. 

Just thought of this:

You may notice (sooner or later) that Fedora and Korora do not have an update notification enabled by default to tell you about updates. At least the XFCE versions didn't. At first, I thought there just wasn't one. Then I found quite by accident that it can be enabled in Yumex from Preferences > Status Icon Tab. Just turn all the switches to ON. You can also make a couple of time settings in there too. This all works very reliably.

---

### Post by RobGoss on 2016-07-08
Dennis does [COLOR=#000000]**Korora **have a software center I have it install but don't see any[/COLOR]

---

### Post by Dennis N on 2016-07-09
> **RobGoss said:**
> Dennis does [COLOR=#000000]**Korora **have a software center I have it install but don't see any[/COLOR]

I hope the installation went well. In Yumex, the closest you can get is to search by Categories - for example "Sound and Video". In it's main menu, select "Groups". 

I'm sure (unless it is very well hidden) there is no equivalent of "Ubuntu Software Center" with longer descriptions and star ratings and so on in either Fedora or Korora. 

Korora's roadmap on their web site indicates they have plans "in some future release" for a Software Center.

---

### Post by RobGoss on 2016-07-09
> [COLOR=#000000]I hope the installation went well. In Yumex, the closest you can get is to search by Categories - for example "Sound and Video". In it's main menu, select "Groups". [/COLOR]

[COLOR=#000000]Yea the installation when well on my Dell latitude D610 in fact, I'm surprised how fast this OS is I'm loving it, I'm trying to install it also on an old Toshiba laptop but I'm not having any luck it loads up to the desktop but after that the whole system freezes.

The laptop had about 2 GB of ram so I don't know if it's a graphic card issue....

Thanks so much for your help Dennis much appreciated [/COLOR]

---

