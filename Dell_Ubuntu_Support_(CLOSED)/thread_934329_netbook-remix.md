---
title: "netbook-remix"
date: 2008-09-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nwgray on 2008-09-30
Anyone else running netbook-remix on the Mini? I just got it running and it's great so far. I did have to set visual effects to none but I wasn't too worried about running compiz on this thing anyway. 

I have been unsuccessful in finding the ume-config-netbook package. I added the launchpad repos to sources.list but it still doesn't show up.

---

### Post by jbloodwo on 2008-09-30
this is kind of a stupid question but did you add the folowing sources to /etc/apt/sources.list
and run sudo apt-get update

---

### Post by brnetonboy on 2008-09-30
Where did you get netbook-remix? I ordered the Dell Ubuntu version (which comes with remix preinstalled, I think), but they weren't going to ship until October 30! So I am going to buy the XP version and install Ubuntu myself.

Is this what you did? Where did you get it from, I thought Dell hadn't finished yet, thus the delay?

---

### Post by jbloodwo on 2008-09-30
Dell is(are) shipping a form of the netbook remix.  
the main diffrence that i am aware of sofar is dell has chosen to use a custom launcher bar in paplce of the launcher screen that the standard netbook remix has.  
the main project page for the generic netbook page is here. 

[https://edge.launchpad.net/~netbook-remix-team](https://edge.launchpad.net/~netbook-remix-team)

there may be other customazations that have been made by dell to make the system better operate with the mini... 
I am planning on doing a fresh reinstall of 8.10 and add netbook 
and a du -h on both the mini and public netbook.

I am thinking about doing a clean of the archived .deb's on both systems and then doing a 
ls -lar />netbook.txt
and 
ls -lar />mini9.txt
then run a dif on the 2 files to see what the changes actually are between the public version and the dell version.

---

### Post by brnetonboy on 2008-09-30
> **jbloodwo said:**
> Dell is(are) shipping a form of the netbook remix.  
the main diffrence that i am aware of sofar is dell has chosen to use a custom launcher bar in paplce of the launcher screen that the standard netbook remix has.  
the main project page for the generic netbook page is here. 

[https://edge.launchpad.net/~netbook-remix-team](https://edge.launchpad.net/~netbook-remix-team)

there may be other customazations that have been made by dell to make the system better operate with the mini... 

Thanks for clarifying... I had thought that "Remix" was the Dell version of Ubuntu. I am interested in "Dell Remix" because of what you mentioned and of course because of the guaranteed hardware compatibility! But also because I heard it will have some non-free codecs for audio and video and some other things.

I suggested to Dell that they sell Dell Remix seperately when it becomes available. Here's the ideastorm page:


[CENTER][URL="http://www.ideastorm.com/article/show/10092923/Sell_install_discs_for_Dells_customized_version_of_Ubuntu_Remix_for_Mini_9"]
http://www.ideastorm.com/article/show/10092923/Sell_install_discs_for_Dells_customized_version_of_Ubuntu_Remix_for_Mini_9
[/URL][/CENTER]

Maybe if enough people ask Customer Service for the discs, they'll make them available.

---

### Post by jbloodwo on 2008-09-30
for a good defination of what a remix is see 
[http://www.canonical.com/projects/ubuntu/nbr](http://www.canonical.com/projects/ubuntu/nbr)

---

### Post by anjilslaire on 2008-10-01
There's a bit more than just some GUI customizations, including specific optimizations for the Atom CPU and other hardware:
[http://ubuntuforums.org/showpost.php?p=5748408&postcount=47]("http://ubuntuforums.org/showpost.php?p=5748408&postcount=47")

> 
A lot of customization has been put into place that ties the Ubuntu install that's shipped with them to the exact device. Things such as controlling Bluetooth and WLAN, being built for the atom's architecture (LPIA), and a lot of applications had to have their UI modified to be able to fit on such a small resolution. Some of this customization will start to show up in Ubuntu 8.10, some won't . Some of it is just wed very specifically to this hardware.

Also, like Dell laptop & desktop machines, if you purchase this with Linux preloaded, you will be receiving a codec package that adds support for a handful of codecs that don't normally work well.


---

### Post by pHreaksYcle on 2008-10-01
Atom processor compatibility does NOT come from dell, just their UI. It's just a package that you can get (or not, haven't actually tried to find it yet) called Ume-config-netbook.

---

### Post by anjilslaire on 2008-10-01
I didn't mean necessarily that the CPU optimizations came from Dell specifically, just that the version running on these things is *not* just gui changes. I believe Canonical is working with Dell to get this thing optimized specially for the Mini 9. The quote above is from one of the Ubuntu devs, so its pretty reliable.

---

### Post by nwgray on 2008-10-01
> **jbloodwo said:**
> this is kind of a stupid question but did you add the folowing sources to /etc/apt/sources.list
and run sudo apt-get update

Yep - tried it yesterday and this morning. No luck. I just wonder what the package actually does. Am I missing something extremely cool? So far, the remix is awesome. Maximus runs well - all windows are maximized automatically and show up well except for, so far that I've found, some prefs windows including the login window. I wanted to change the gdm theme. The window opens up but I can't see the bottom third of it aned I can't scroll down. If I hook up an external monitor, it shows up. 

No biggie, just interesting. Seems as if the prefs windows aren't "obeying" maximus.

---

### Post by pjalegria on 2008-10-10
Does anyone now how to acess add/remove software on Ubuntu Remix???

---

### Post by brnetonboy on 2008-10-10
> **pjalegria said:**
> Does anyone now how to acess add/remove software on Ubuntu Remix???

Nobody else has the Remix on the Mini yet--except you! But I would guess that you can open a terminal and type "synaptic".

Does the Mini come with Ubuntu Re-installation CDs? What do they say on them?

---

### Post by 2damncommon on 2008-10-10
System -> Administration -> Synaptic Package Manager works on a default 8.04 Ubuntu.

The /etc/apt/sources.list has to have the the repositories listed and you would need a working internet connection.

---

### Post by njpatel on 2008-10-17
I don't want to unnecessarily bump the thread, so sorry that I have, but I thought it's important for anyone else who stumbles across this.

Please _do not_ install ume-config-netbook. I realised yesterday that I'd left it on the UNR front page even though I removed it from the ppa (a "Doh!" moment if there ever was one).

For the inquisitive, it's a package that targets a particular device based on atom, the description was wrong. Also, it added its own modules and X set-up which wouldn't un-install correctly. Hardy already has great support for these chipsets, so you don't need a special configuration.

Sorry for all the confusion!

---

