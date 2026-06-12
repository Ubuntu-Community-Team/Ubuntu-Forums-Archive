---
title: "Programs Disappearing!"
date: 2009-05-20
forum: General Help
---

### Post by a_white92 on 2009-05-20
I don't Know why this is happening, but Skype and Wine have disappeared! They didn't happen at the same time. my brother had the same problem. were both running Ubuntu 9.04. wine is gone and my programs are still there but they don't run... I know i didn't remove them...

---

### Post by AlexsAntidote on 2009-05-20
Could you please clarify what you mean by "not there"? Are you referring to the menu items for those programs? Or do you mean they actually do not exist on your system?

Please open your terminal and enter the following:
```
dpkg -l |grep wine
```
and
```
dpkg -l |grep skype
```

And post the output. If the packages have been removed from your system there wont be any output. If they are still there it will give you some type of output.

---

### Post by a_white92 on 2009-05-20
Here is the output:
```

dpkg -l |grep wine
aaron@aaron-laptop-ubuntu:~$ dpkg -l |grep wine
rc  libkwineffects1                                                4:4.2.2-0ubuntu2                         library used by effects for the KDE 4 window manager
rc  wine                                                           1.0.1-0ubuntu6                           Microsoft Windows Compatibility Layer (Binary Emulator and Library

``````
dpkg -l |grep skype
aaron@aaron-laptop-ubuntu:~$ dpkg -l |grep skype
rc  skype                                                          2.0.0.72-1                               Skype - Take a deep breath


```
When i try to run a program that runs through wine it don't work anymore.

---

### Post by AlexsAntidote on 2009-05-20
It looks like Wine and Skype are still installed on your machine, however they appear to be Release Candidate versions (RC's).

When did you first notice this happening? Was it after an update? Did you upgrade from Intrepid to Jaunty? 

Are you using "bleeding edge" settings for your repositories (so that you're using RC's all the time)?

Have you tried:
```
sudo apt-get update
sudo apt-get upgrade
```

You may also want to check for broken packages and broken dependencies

```
sudo apt-get -f install
sudo apt-get check
```

---

### Post by a_white92 on 2009-05-20
[LIST=1]
[*]For me this just happened to day, but it happened to my brother like yesterday.
[*] No, It Was not after an update.
[*] and no, I Did not upgrade from Intrepid to Jaunty. I switched from Windows to Ubuntu Linux 9.04 Jaunty Jackalope about a month ago.
[/LIST]
 > Are you using "bleeding edge" settings for your repositories (so that you're using RC's all the time)?[INDENT]O_o I have no idea... but if i am how would i know?[/INDENT]

---

### Post by AlexsAntidote on 2009-05-20
OK thanks for clarifying all of that. My next question is, did you upgrade to Jaunty (9.04) before the official release?

type the following in terminal and post your output:
```
lsb_release -a
```
That should tell you what version of Ubuntu you are running.

To check what settings you have on your repositories (and if you're set to "bleeding edge" go to 

system menu -> administration -> software sources

once software sources is open go to the updates tab, the first section has 4 check boxes, the first 2 should be checked. if you are "bleeding edge" you will likely have all 4 checked. If you are confused on that you could just post a screenshot.

---

### Post by a_white92 on 2009-05-20
Here is my output:
```

aaron@aaron-laptop-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:       Ubuntu 9.04
Release:           9.04
Codename:          jaunty

```And here is a screen shot:

---

### Post by rudy.b on 2009-05-21
Actually, the "rc" in the dpkg display means that the packages have been marked for removal, but the config files are still available.  You should be able to re-install them using the package manager:  System > Administration > Synaptic Package Manager.

---

### Post by AlexsAntidote on 2009-05-21
> **rudy.b said:**
> Actually, the "rc" in the dpkg display means that the packages have been marked for removal, but the config files are still available.  You should be able to re-install them using the package manager:  System > Administration > Synaptic Package Manager.

Ah that makes sense, thanks for clearing that up for us Rudy.b, I learned something new there.

---

### Post by rudy.b on 2009-05-21
No problem, but that still doesn't solve the mystery of how the packages were removed in the first place. 

:-k

---

### Post by pbpersson on 2009-05-21
I hope you did not run the Computer Janitor

---

### Post by a_white92 on 2009-05-22
I did not run the Computer Janitor, not that i know of...
And thanks [rudy.b]("http://ubuntuforums.org/member.php?u=826823") for clearing that up for us... 
and now one of my ganes is gone!

But let me try this, I will reinstall them, and keep track of what i do on my computer, and if they disappear again then maby ill have something to work with. but if you figure out something, Please let me Know.

Thank You All For Your help, It was greatly Appreciated. :D

---

### Post by pererik87 on 2009-12-24
I also have programs dissapearing. vlc, kdenlive and blender.
to easy to just reinstall, but how they disappear is a mystery...

---

### Post by lite1979 on 2010-01-04
I just lost wine, it seems.  The only thing I did recently was boot into an older version of Kubuntu that I have on this same machine to burn a DVD (too lazy to install necessary libraries to do it in Ubuntu, and I love K3B...).

output of 'dpkg -l | wine':

"The program 'wine' can be found in the following packages:
 * wine
 * wine1.2
 Try:  sudo apt-get install <selected package>
 wine:  command not found"

Running Ubuntu 9.10 karmic

Weird thing is I can still locate it in the menu under Applications > Programs > Steam > Half-Life, but the Configure, Uninstall, and Browse C:\ Drive options are all gone...

All I use wine for is playing Half-life in Steam

It doesn't quite play well yet because my sound is terrible and my wireless network is poo-poo here, but I'd still like to play!


Edit (later that night...)

Used Synaptic to install wine1.2 and it appeared in the menu with all the options.  I didn't have to configure anything and my game started right up from the menu...

---

### Post by lite1979 on 2010-01-06
Figured I'd follow up here.  No problems since last post.  I didn't have to re-install Steam or Half-Life, and the sound issues that I had previously are practically gone.  I'm using Alsa for Wine, and I can have pandora running and play half-life at the same time with good sound for the most part, though after playing for about a half-hour last night, I noticed that sound started to be delayed in the game; not sure why yet.

---

### Post by Dr Sketch on 2010-01-18
Just curious if anyone has found anything out about why this is happening?  It has been happening with me as well (I'm not set to bleeding edge), and usually with the same few programs every time.  The one I notice most is Gourmet Recipe Manager, but it's happened with others as well.  It's not too hard to re-install, but it would be nice to know why they keep disappearing like this.  The config files are thankfully still there, so I don't have to rebuild my database every time...  Anyone?

---

