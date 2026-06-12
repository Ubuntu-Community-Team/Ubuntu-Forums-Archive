---
title: "Ubuntu 11.04 Flickering black screen"
date: 2011-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TravisMoehring on 2011-08-29
Alright, I am not as Linux literate as most of the users here, but at least I'm literate. I have an issue with Ubuntu 11.04 Natty Narwhal. I have installed it on my computer alongside Windows 7. I have dual booted Ubuntu and Mint before but never on this computer. While I may not understand the terminology you provide, if you dumb it down enough, I think I'll manage. I'm posting from withing Ubuntu 11.04 right now but I am in failsafex. If that helps, I am glad. It may narrow down the problems. I am also going to include an image of the error I am getting...if it even is an error. 

[IMG]http://www.freeimagehosting.net/bf914[/IMG][thumb]http://xs.to/media/111767[/thumb]

Below is the exact computer I am using.
http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=100006740&IsNodeId=1&bop=And&ActiveSearchResult=True&CompareItemList=32|34-200-296^34-200-296-TS%2C34-214-278^34-214-278-TS

---

### Post by TravisMoehring on 2011-08-29
Bump? I hate to be one of those guys and I know you guys have more pressing issues, but maybe a referral to a thread meeting the same issues as me?

---

### Post by rectec794613 on 2011-08-29
Could you describe your issue a little more? It looks like a typical Linux bootup just without a boot screen. Do you want to see the bootscreen?

---

### Post by TravisMoehring on 2011-08-29
Oh sorry about that. It loads up the purple screen with the words Ubuntu and the five dots blinking in succession, then the screen flickers slowly (about once per second on and off) and then that screen pops up and then the OS goes no where. It stays put right there and doesn't do anything more.  

I have waited a full 2 minutes but if I maybe need to wait more I would feel pretty foolish. 

If you have any other questions I will try to answer them to the best of my abilities. I just don't really know what information I have is useful.

---

### Post by rectec794613 on 2011-08-29
Try posting the contents of boot.log located at /var/log/boot.log. Just click on the file, it should open up in the text editor. Copy the contents and post them to [http://paste.ubuntu.com/](http://paste.ubuntu.com/) 

Hopefully we can get an expert on the subject. I can examine it to the best of my ability, but fixing the problem is a whole different story.

---

### Post by rectec794613 on 2011-08-29
The link you provided for the system specs doesn't work. Could you please post the product page instead of a comparison? Thanks. 

I have some suggestions ready but I can't be sure until I know what computer you have.

---

### Post by TravisMoehring on 2011-08-29
> **rectec794613 said:**
> The link you provided for the system specs doesn't work. Could you please post the product page instead of a comparison? Thanks. 

I have some suggestions ready but I can't be sure until I know what computer you have.

Oh wow. Really sorry about that. I should have at least checked the link :P
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834200296](http://www.newegg.com/Product/Product.aspx?Item=N82E16834200296)

---

### Post by rectec794613 on 2011-08-29
Nice. Ok so do you have the Nvidia drivers installed? If not press ctrl+alt+T to open up a terminal window and type this in to install them:
```
sudo apt-get install nvidia-current
```

Restart and see if that works.

Not much else I can do without examining your boot log. Just press alt+f2 and type this in to open up the file manager:
```
nautilus
```

Click "Go" from the menu, click "Location", then type /var/log, then look for the boot.log file, click it, copy it, paste it to [http://paste.ubuntu.com](http://paste.ubuntu.com)

Click "Paste!" then copy the URL from your browser. Finally paste the URL here.

The problem could also be related to Unity, but that's another story. If all else fails. we'll get into Unity.

---

### Post by TravisMoehring on 2011-08-29
> **rectec794613 said:**
> Nice. Ok so do you have the Nvidia drivers installed? If not press ctrl+alt+T to open up a terminal window and type this in to install them:
```
sudo apt-get install nvidia-current
```

Restart and see if that works.

Not much else I can do without examining your boot log. Just press alt+f2 and type this in to open up the file manager:
```
nautilus
```

Click "Go" from the menu, click "Location", then type /var/log, then look for the boot.log file, click it, copy it, paste it to [http://paste.ubuntu.com](http://paste.ubuntu.com)

Click "Paste!" then copy the URL from your browser. Finally paste the URL here.

The problem could also be related to Unity, but that's another story. If all else fails. we'll get into Unity.
Alright, thanks. I'll try both later on. I need to get to bed for school tomorrow and stuff. Problems we all have. I'll report back tomorrow with more details and I'll have tried your solutions.

So far you've been a great help and give this forum a very inviting feeling for us "not quite new to Linux but still don't have it down" folks.

---

### Post by rectec794613 on 2011-08-29
Haha, thanks. I try my best. See you tomorrow, hopefully we can fix this.

---

### Post by TravisMoehring on 2011-08-30
Alright, the first command returned this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```The boot.log contained the following:
```
fsck from util-linux-ng 2.17.2 
/dev/sdb5: clean, 162597/14827520 files, 1733773/59301632 blocks 
 * Starting network connection manager[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting configure network device[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting Mount network filesystems[74G[ OK ] 
 * Starting System V initialisation compatibility[74G[ OK ] 
 * Stopping Mount network filesystems[74G[ OK ] 
 * Starting Bridge socket events into upstart[74G[ OK ] 
 * Starting configure network device[74G[ OK ] 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 * Starting AppArmor profiles       [80G  [74G[ OK ] 
Skip stopping firewall: ufw (not enabled) 
 * Stopping System V initialisation compatibility[74G[ OK ] 
 * Stopping Bridge socket events into upstart[74G[ OK ] 
 * Stopping Uncomplicated firewall[74G[ OK ] 
 * Starting set console keymap[74G[ OK ]
```
[http://paste.ubuntu.com/678160/](http://paste.ubuntu.com/678160/)

---

### Post by rectec794613 on 2011-08-30
Ok. Here's some suggestions. There could be something wrong with LightDM, which is Ubuntu's new login screen basically. Go into Synaptic by typing this into a terminal:
```
sudo synaptic
```
Provide your password, type *lightdm* into the quick search. Choose "Mark for complete removal", then after it's removed, choose "Mark for installation". Reboot and see if it's fixed.

And if *that* didn't work, try using GDM instead. Remove LightDM, search for "gdm" then mark it for installation.

If that doesn't work, type this into the terminal to reset Unity back to it's factory settings:
```
unity --reset"
```

If all else fails, I would just reinstall Ubuntu. Or try Kubuntu.

---

### Post by rectec794613 on 2011-08-30
Also a temporary fix would be to boot into recovery mode by selecting it from the boot menu. Choose "Resume normal boot", login, then enter *startx* to boot into Ubuntu.

---

### Post by TravisMoehring on 2011-08-30
Okay. I booted into failsafex and when I go to synaptic and type in LightDM and click the check box, the only available option is "Mark for Installation".  Should I still proceed?

---

### Post by rectec794613 on 2011-08-30
Great. I think we hit the nail on the head here. First search for gdm and kdm and see if those aren't already installed. If not, go ahead and install LightDM.

---

### Post by TravisMoehring on 2011-08-30
Well it shows gdm as already installed. Should I uninstall it or just install both?

---

### Post by rectec794613 on 2011-08-30
First I would mark it for reinstallation, that usually fixes my login problems. If that doesn't work then remove it and install LightDM.

---

### Post by rectec794613 on 2011-08-30
Hold up... just got an idea. If my previous suggestions didn't work, boot into recovery mode, choose resume normal boot, login, then type either *gdm start* or *lightdm start* depending on which you have. We need to figure out why the login screen won't start. If nothing happens, take a picture of the error message. If something does happen, we'll need to edit the startup file.

---

### Post by mikewhatever on 2011-08-30
I'd strongly advise against installing LightDM in Natty, which uses GDM as the default login manager. The first Ubuntu version to switch to LightDM is Oneric.

_To the OP:_
You might want to try running the following command and then rebooting:
```
sudo nvidia-xconfig
```

---

### Post by rectec794613 on 2011-08-30
Finally, some backup. My bad about LightDM, I was pretty sure that it was gdm's replacement, but I guess not yet. I'll be monitoring this thread, but I hope you can take over mostly. Good luck with Ubuntu, Travis.

---

### Post by TravisMoehring on 2011-08-30
Thanks for the help you two. Really. I did some experiments to try and narrow down my issue and I've hit a nerve. I did an install without checking the updates and third party stuff and natty booted fine. In my lapse in judgement (seeming to forget the scientific method, and possibly thinking I just got lucky) I decided to both update the stuff in synaptic and install the nvidia stuff, and it is now repeating it's symptoms. So it's either a problem with nvidia or a problem with one of the update packages. Hope that helps.

---

### Post by TravisMoehring on 2011-08-30
A quick question though, does the installer install the nvidia driver if you check off both install updates and third party stuff?

If not, then the problem is definitely one of the packages that are updated. If it does, then it could very well be either one of them.

Edit: So I erased and reinstalled 11.04 again and didnt check the two boxes. I installed the experimental nvidia driver instead of the other one and the error isn't happening.  In true scientific tradition, I installed the other and, sure enough, the problem returned.  My issue is with the other driver, not the updated packages or the experimental Nvidia driver.

---

### Post by mikewhatever on 2011-08-31
> **rectec794613 said:**
> Finally, some backup. My bad about LightDM, I was pretty sure that it was gdm's replacement, but I guess not yet. I'll be monitoring this thread, but I hope you can take over mostly. Good luck with Ubuntu, Travis.

Hm..., why should I take over?

---

### Post by TravisMoehring on 2011-08-31
Okay guys. I figured out that the issue was with the proprietary drivers from Nvidia and so I avoided them.  Unfortunately I didn't like the Unity desktop very much and this was the only reason I left 10.10 at all.  I have reinstalled 10.10 and am happy with my setup now.  Thanks for all your help.

---

