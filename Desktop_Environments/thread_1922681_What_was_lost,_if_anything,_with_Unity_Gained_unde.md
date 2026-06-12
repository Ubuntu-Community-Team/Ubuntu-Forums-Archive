---
title: "What was lost, if anything, with Unity? Gained underneath?"
date: 2012-02-09
forum: Desktop Environments
---

### Post by Odyssey1942 on 2012-02-09
I installed 11.10 on a new build, got completely frustrated by the unfamiliarity and went back to 10.04 (which I love)

It occurs to me that I may have misjudged Unity, which I do not love, and which seemed to have lost the lean and productive look of 10.04. I have questions that may help me better understand it.

Can the overly (and uselessly IMO) large icons in the launcher (and the launcher) be reduced in size and fixed through reboots at the smaller size?

What does the launcher replace? I identify: 

Applications/Places/System in the upper left of the top panel (in 10.04) Where are these functions located now? To the extent that they are now in the launcher, would you say that there are extra steps to get to the functions contained within, about the same or fewer?

Does the top panel continue to function as in 10.04 in that you can put small icons for programs that you use frequently? (One of the big advantages of the panel in 10.04 is that the icons [i.e., shortcuts] are small and one click from opening vs multiple clicks in the launcher.)

Can you put shortcuts to files, folders, drives, and programs on the desktop just as in 10.04?

The Workspace selector in the launcher only showed 4 workspaces. Can there be more workspaces? Can they be made "constant" (through successive reboots) at xy (larger than 4) numbers? I got the impression that there can be more than 4 but they are dynamic in that when you need one more, it can be opened. If constant, can they be named?

In general terms (e.g. more stable? faster? etc), what improvements to Ubuntu came in 11.10 vs 10.04? In my 10.04, I have 6 constant workspaces, each for a specific purpose, which allows me to have a grand total of approx 20+ browser windows, each with multiple tabs, all supported by 8GB of RAM, open all the time. Lean, quick, productive!

I will appreciate your thoughts.

---

### Post by nothingspecial on 2012-02-09
1. Install compizconfig-settings-manager, go to the unity plugin and change the icon size (in 12.04 this can be done from the settings window)

2. Press Super-F to get something similar to the places menu and Super-A for applications.

3. Open a terminal and type ```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
``` Then log out and back in again.

4 I think so but not sure (I like a clean desktop).

5 Again in compizconfig-settings-manager go to the section labled "General". In there go to the desktop size tab. You can set the amount of workspaces there. For example, if tou set Horizontal 4 and Vertical 2 you will get a 4x2 grid of 8 workspaces.

---

### Post by Odyssey1942 on 2012-02-09
I have waited to reply hoping that there might be additional comments. Craig, I seek clarification on a couple of points please.

1. Can the launcher size also be reduced or just the icons in the same large space? Does this survive a reboot or does one have to manually set each after each reboot?

2. "Super" is the key with the Windows logo on it?

3. What does this do please?

5. Does this setting survive a reboot or does one have to manually set each after each reboot?

Many thanks.

---

### Post by grahammechanical on 2012-02-09
Hi

The icons in the launcher and the width of the launcher are in proportion to each other. In other words the Launcher shrinks in width as well as the icons. You can also change the opacity of the Launcher and the top panel for that matter so that it becomes invisible. And yes, it all survives reboot.

The super key is the one with the Microsoft flying windows icon on it. In 12.04 a tap on the super key brings out the Dash. Holding down the super key brings out an overlay that has keyboard short cuts on it for reference. Also, the icons on the launcher get numbered from the top donw so that we can press a number to load that program.

As regards the top panel it is similar but the Add to panel function is no longer available. Instead we install application indicators.

This is what is some of what is available:

[http://askubuntu.com/questions/30334/what-application-indicators-are-available]("http://askubuntu.com/questions/30334/what-application-indicators-are-available") 

In the Dash there are four icons at the bottom representing - Home - applications - Files - Music.

Click on the icon for home and we get Recent Apps - Recent files - Downloads (recent downloads).

Click on the icon for Applications and we get Recently Used - Installed - Apps Available for Download.

Click on the icon for Files and we get Recent - downloads - Folders (recently used folders)

Click on the icon for Music and we get Songs - albums

With all these we get the option to see more files. Keep in mind I am describing what is available at present in 12.04.

With all that RAM you must also have massive amounts of disk space. Why don't you create another partition and install 12.04 alpha 2 on it or the beta when it comes out? Then you can see for yourself and set up the OS the way you like it before upgrading your 1.04 install.

But if you are not prepared to put in some effort to learn a different way or doing things then stay with 10.04.

Regards.

---

### Post by prusswan on 2012-02-10
Stick with 10.04, or chart a gnome-based solution around the default Unity option. Unity is meant for a group of users who are able to pick it up without much thinking, if you have to think then you are unlikely to be the intended target audience.

---

### Post by Odyssey1942 on 2012-02-10
Prusswan, Thanks for your advice. That's exactly what I am doing for now, but I am concerned that I will not be participating in the improvements in successive versions of Ubunutu (especially underneath the hood.)

For both Prusswan and Graham (thanks to you also), I am yet to be convinced that Unity is an advance. It seems to me to be an Apple knock-off that adds extra steps to what I am accustomed to in 10.04.

I don't have a problem specifically with the Unity launcher, it's what the community has lost because of it. I can see icons in the top right hand corner of the 11.10 upper panel (which clearly remains), so that "shortcut" functionality obviously remains there. Unfortunately we cannot now utilize it as before to place our own preferred icons. For example, in my 10.04, I have icons for the terminal, for word and text processors, browsers, calculator, system monitor, and others, and have not used more than 1/4 of the available space on my screen. All I have to do is click on the desired icon.

To access these in Unity, I have to first go to the launcher (and to retrieve it from hiding if I have put it into hiding to get my desktop space back) to find an icon that I have to click on to find the icon that I want. So that is at least two, probably three in my case, extra steps to get to something that I can see right now without having to click on anything first. How is this an improvement?

I really don't have a problem with the launcher as a dumbed down option for those who like/need it. But why can't the still available panel be used as before?

Finally, I still don't know if you can customize your 11.10 desktop by placing shortcuts to files, folders, drives, etc on it, or have the powers that be decreed that MY desktop must be clear?

---

### Post by prusswan on 2012-02-10
The available panel as you understand it will exist as the gnome-session-fallback, or gnome-shell when it is ready. These can all be considered Gnome3 variants. They will nearly be the same as Gnome2 in 10.04 which is no longer supportable.

Unity is supposedly designed to embrace users of smaller screen devices, where the larger icons are easier to tap on. A few quick taps on a phone is cheaper compared to mouse clicks. Desktop users can try to adjust to it (and that's what the Unity designers are hoping for), but that may not be their best course of action considering there are alternatives closer to what they are already accustomed to.

---

### Post by Odyssey1942 on 2012-02-10
That line of thinking from above is misguided at best.

There are smartphones, tablets, and desktops/portables. I have had a smartphone for years, but when I come through the door of my home or my office, it only gets picked up to use as a phone.

If I want to get work done, I head straight for one of my Ubuntu or Windows desktops (one w/16GB RAM, the other 8GB), if I want portability for reading, not working, I pick up my tablet (WiFi only), and when I leave again, out comes the phone as a very weak substitute even for email.

A smartphone is years away from becoming a workplace. It will require voice input that is as effective as a keyboard (not even close to being here) and some sort of readability to approximate my 24 inch monitor (maybe never).

And which manufacturer or platform does Ubuntu target for using Unity anyway? It would never even occur to me to consider using something like Ubuntu on my android phone.

Finally, again do you know if icons can be placed on the Unity desktop?

Thanks for listening and your thoughts.

---

### Post by Version Dependency on 2012-02-10
> **Odyssey1942 said:**
> Finally, again do you know if icons can be placed on the Unity desktop?

Icons are able to be placed on the desktop.  If, for some reason you can't do this, then it was probably disabled during an upgrade.  Go to dconf-editor, and navigate to org > gnome > desktop > background.  See if the show-desktop-icons option is disabled.

---

### Post by chejose on 2012-02-11
About the best solution for us who refer the old Gnome 2 simplicity is to go to Mint. 

José

---

### Post by Odyssey1942 on 2012-02-11
Thanks, Chejose. In fact I am actively looking into Mint 12 with Cinnamon, to try to keep up with Ubunutu's "under the hood" improvements, while keeping closer to the look and feel of U10.04.

Does anyone have a clear idea of what Ubunutu is trying to accomplish with respect to making Ubunutu more "mobile compatible" (if that is the right description), or as Prusswan states: "Unity is supposedly designed to embrace users of smaller screen devices". What small devices? Smartphones and tablets all come with their own O/S. How does Unity figure into those smaller devices unless Ubuntu IS the O/S? How might that happen?

I'm just baffled by this Unity thing and want to try to understand what Canonical is thinking/planning. If it is to make Ubuntu more friendly to novices, I think that is a great option to present. But cannot the more powerful functionality that existed pre-Unity be preserved as another option for those who want a more efficient O/S?

Please weigh in and describe the logic of Unity.

---

### Post by nothingspecial on 2012-02-11
Or try Xubuntu

[IMG]http://img84.imageshack.us/img84/3082/screenshotat20120206114.png[/IMG]

---

### Post by Odyssey1942 on 2012-02-11
NS, that looks nice and clean (i.e., no launcher taking up an inordinate amount of real estate) and I see there is a top panel. Can one place icons (shortcuts) on the top panel?

What version of XUbuntu is that? Does Xunbuntu follow the same release schedule as Ubunutu?

In very general terms, what is/are main negative/s?

---

### Post by nothingspecial on 2012-02-11
That is Xubuntu 11.10 customized to look as much as possible like Ubuntu 7.10

Xubuntu follows the same release schedule as Ubuntu and is an official derivative. It uses the same repositories as Ubuntu and therefore has everything that Ubuntu has available to install should you choose.

It is fully supported here, on irc, in launchpad etc.

I'd suggest you try it, bearing in mind that it looks nothing like my screenshot when you first install it :)

---

### Post by u2nTu on 2012-02-22
> **Odyssey1942 said:**
> ...**I am yet to be convinced that Unity is an advance.** It seems to me to be an Apple knock-off that adds extra steps to what I am accustomed to in 10.04. ...

To access these in Unity, I have to first go to the launcher (and to retrieve it from hiding if I have put it into hiding to get my desktop space back) to find an icon that I have to click on to find the icon that I want. So that is at least two, probably three in my case, extra steps to get to something that I can see right now without having to click on anything first. [B]How is this an improvement?
[/B] 
I really don't have a problem with the launcher as a dumbed down option for those who like/need it. But [SIZE=4]**why can't the still-available panel be used as before?**[/SIZE] ... 

Well said.

People prefer choices. Why not let the user select between the new app-indicator functionality and the old standard?

The idea of a disappearing side panel is fine, but not only is **task switching now grievous**, the current top panel is **a long stretch of wasted screen space**. Why not let the user choose? Make everybody happy.

Have to say that I've tried to embrace Unity. **I want to like it.** It's just goofy and stupid! Please let us have a 10.xx UI option!

Almost went on without posting because this horse is long dead. For such an incredible OS, it is utterly amazing the front end is going in the direction it is.
 

[SIZE=1] (bold and text size added to original quote)[/SIZE]

---

