---
title: "Best way to install XFCE (Xubuntu) alongside (Unity) Ubuntu 13.10?"
date: 2013-11-20
forum: Desktop Environments
---

### Post by foxj.1994 on 2013-11-20
Hi guys. This is my first post on this forum with this account (my "Ubuntu One" account), however I have posted on here before with an old account back when I was using ubuntu maybe 4-5 years ago. I'm very much a beginner; I went back to windows after using ubuntu those years ago because I preferred it for gaming and was a big gamer back then. I've started to get back into linux, however, and have tried Linux Mint alongside windows, and am now back on to Ubuntu alongside windows.

I'd like to try out the XFCE Desktop Environment to see if I prefer it to Unity.

I understand that this question has been asked before on here, and I did search the forums and found a few threads about it, but none were tailored to my particular question. So, my question is this:

What is the best way to install XFCE alongside Unity? I understand that I could use a Xubuntu live-CD, but I'm looking for a way to work with my current install without doing that. I've heard people mention doing:
```
sudo apt-get install xubuntu-desktop
```
And I've also heard that there may be a way to install XFCE via the software centre? Which is the best way?

Also--and this is the reason for me creating a new thread rather than doing more research--on this site here: [https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative) , it is suggested that you run the command:
```
sudo apt-get remove nautilus gnome-power-manager compiz compiz-gnome unity unity-* unity8* hud zeitgeist zeitgeist-core python-zeitgeist libzeitgeist* activity-log-manager-common gnome-control-center gnome-screenshot
```
in order to "prevent system pollution problems".
I was wondering if you could enlighten me as to what exactly this means? Why should I remove compiz, for example? I want to keep compiz installed for my XFCE DE, and on top of that, I will be running Unity alongside XFCE, so I don't particularly want to remove anything that I currently have installed for my Unity setup, because I may be switching between the two regularly.

Thanks in advance, and I'm sorry if this question (particularly the last part) *has*&#8203; been answered before.

---

### Post by vasa1 on 2013-11-20
> **foxj.1994 said:**
> ...
Also--and this is the reason for me creating a new thread rather than doing more research--on this site here: [https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative) , it is suggested that you run the command:
```
sudo apt-get remove nautilus gnome-power-manager compiz compiz-gnome unity unity-* unity8* hud zeitgeist zeitgeist-core python-zeitgeist libzeitgeist* activity-log-manager-common gnome-control-center gnome-screenshot
```
in order to "prevent system pollution problems". ....
Hi, did you contact the author of what you've quoted? Generally, the person who wrote something would be best placed to explain why something was written.

As for the other part, installing via apt-get or Synaptic or the software center should yield the same results if you use default settings. So I'm not sure why you feel that one or the other would be "better".

---

### Post by philinux on 2013-11-20
@foxj.1994

By installing xubuntu-desktop you'll be able to choose the xubuntu session at login from the Gear icon.

I would not remove anything until you're decided on the desktop you like.
See this resource. [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by Bucky Ball on 2013-11-20
I think we should get it clear before installing anything: Do you want to install the xfce desktop environment and use it in Ubuntu or do you want Xubuntu instead of Ubuntu?

If you want the former DO NOT install xubuntu-desktop. That is a bad idea no matter how you look at it. You only need to install 'xfce4' and choose it from 'Sessions' when you log in.

Installing *ubuntu-desktop anything on top of an already installed *buntu gives you both (you will effectively have Ubuntu AND Xubuntu with all apps, dependencies and everything else for both). Bloat you don't need, duplication and not what you want. 

If you want just Xubuntu, do a clean install of Xubuntu is easiest and cleanest.

---

### Post by foxj.1994 on 2013-11-20
> **vasa1 said:**
> Hi, did you contact the author of what you've quoted? Generally, the person who wrote something would be best placed to explain why something was written.
I didn't, but as I'm familiar with ubuntuforums being a good place to learn, I figured here might be just as good because the command seems pretty simple. Plus here I'm guaranteed a response fairly quickly; the author might not respond for weeks.
> As for the other part, installing via apt-get or Synaptic or the software center should yield the same results if you use default settings. So I'm not sure why you feel that one or the other would be "better".
Well I referred to that specifically because I had seen people recommending installing "xubuntu-desktop" via command-line, where others recommended installing "XFCE<insert_version_number>" via the software center. I didn't intend it to be a question of command-line vs software centre, considering one's just a graphical extension of the other. Perhaps I worded it badly.

> **philinux said:**
> @foxj.1994

By installing xubuntu-desktop you'll be able to choose the xubuntu session at login from the Gear icon.

I would not remove anything until you're decided on the desktop you like.
See this resource. [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)
> **Bucky Ball said:**
> I think we should get it clear before installing anything: Do you want to install the xfce desktop environment and use it in Ubuntu or do you want Xubuntu instead of Ubuntu?

If you want the former DO NOT install xubuntu-desktop. That is a bad idea no matter how you look at it. You only need to install 'xfce4' and choose it from 'Sessions' when you log in.

Installing *ubuntu-desktop anything on top of an already installed *buntu gives you both (you will effectively have Ubuntu AND Xubuntu with all apps, dependencies and everything else for both). Bloat you don't need, duplication and not what you want. 

If you want just Xubuntu, do a clean install of Xubuntu is easiest and cleanest.

These two posts highlight the issue that (I think) I was primarily confused with. I didn't understand the differences between all of the "recommended" ways of installing: Either via installing "xubuntu-desktop"; via installing "xubuntu-desktop" and then running that command that removes stuff; or via installing "xfce4".

All I want(ed) was to install the Desktop Environment XFCE, and be able to choose between XFCE and Unity on my login screen for Ubuntu (*not* Xubuntu). I can't think of anything I don't like about Ubuntu that Xubuntu's apps, dependencies etc would change. So I guess my problem was not realising that "xubuntu-desktop" installs more than just XFCE (I'd thought maybe it installed a version of XFCE designed for ubuntu or something).


So, with this being said, I take it I'm best to just search the software centre and look up "XFCE" and install it, then log out and log into the XFCE desktop? No removal of any apps necessary?
I'm trying to be very cautious with this because when I ran mint, I installed KDE alongside cinnamon, and after logging in and changing a setting (I forget what the setting was), it crashed my whole installation and I was getting driver errors. In fact that's one of the reasons I changed to Ubuntu with a fresh install, because I couldn't figure out how to fix it even with forum help. (Though the silver lining is I'm now glad it happened and led me to Ubuntu).

---

### Post by philinux on 2013-11-20
@foxj.1994

Glad you've cleared up what you want for yourself.

In software center search xfce4 which is the meta package thats pulls in the required bits for an xfce session at login.

---

### Post by Bucky Ball on 2013-11-20
> **philinux said:**
> 

In software center search xfce4 which is the meta package thats pulls in the required bits for an xfce session at login.

+1. Yep, that's it, and you're done. Log out, choose it from Sessions, log in. ;)

---

### Post by Frogs Hair on 2013-11-20
If choosing the XFCE session consider installing the xfce4-goodies package which provides a number of things you may want including panel indicators, artwork, and some applications. See the description in the software-center .

---

### Post by foxj.1994 on 2013-11-20
Thanks for the help guys :)

Also Frogs Hair, I saw that option after I installed XFCE :( Is there any way to install it afterwards, or should I reinstall it?

I was looking to have the DE look and feel similar to the xubuntu one (i.e. [http://1.bp.blogspot.com/-eRfS24bR4Ic/UH-qJm4W23I/AAAAAAAALAA/MMHmX688a3w/s1600/xubuntu12.10-apps.png](http://1.bp.blogspot.com/-eRfS24bR4Ic/UH-qJm4W23I/AAAAAAAALAA/MMHmX688a3w/s1600/xubuntu12.10-apps.png)) with compiz too. But so far it looks and runs like windows 98, and the changes I make in CCSM aren't affecting anything (enabling wobbly windows in there doesn't make the windows wobble, for example).

---

### Post by philinux on 2013-11-20
Just install the goodies. Log out then back in.

---

### Post by Bucky Ball on 2013-11-20
'xfce4-goodies'. Find it in Software Centre. ;)

I don't actually use it myself but you might find something useful in there.

---

### Post by tbsteinb on 2013-12-17
> **foxj.1994 said:**
> I was looking to have the DE look and feel similar to the xubuntu one (i.e. [http://1.bp.blogspot.com/-eRfS24bR4Ic/UH-qJm4W23I/AAAAAAAALAA/MMHmX688a3w/s1600/xubuntu12.10-apps.png](http://1.bp.blogspot.com/-eRfS24bR4Ic/UH-qJm4W23I/AAAAAAAALAA/MMHmX688a3w/s1600/xubuntu12.10-apps.png)) with compiz too. But so far it looks and runs like windows 98, and the changes I make in CCSM aren't affecting anything (enabling wobbly windows in there doesn't make the windows wobble, for example).

As for theming Xfce, I'd recommend going to youtube and watching different videos by the user LinuxSpatry. Xfce is his favorite desktop environment so he has a lot of different videos on it. The most recent videos he has up there are for Manjaro Linux (an Arch derivative if you don't recognize it), but they will work on Ubuntu just remember to look through the software center, or use "sudo apt-get install [package]"/"sudo aptitude install [package]" which ever you prefer. He has a video series for compiz, and while it is a couple of years old, it still applies.  He recently did a video on installing KDE's oxygen in Xfce to give it a more modern look.

---

### Post by jamvaru on 2014-02-06
i prefer synaptic (use: sudo apt-get install synaptic)
then in synaptic type 'xfce' into the search bar
choose the main xfce and the goodies and whatever else you want
click go
relog, switch session to xfce
...
nice to be able to keep unity, for grins, anyway; it is quite bizarre and seems incomplete to me, but nice to know what people are using (or aren't using, idk)

---

### Post by Bucky Ball on 2014-02-06
*Thread closed.*

Dead support thread resurrected and going wildly off-topic. Nothing to see here. ;)

---

