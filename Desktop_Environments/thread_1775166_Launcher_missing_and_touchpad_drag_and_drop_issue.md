---
title: "Launcher missing and touchpad drag and drop issue"
date: 2011-06-04
forum: Desktop Environments
---

### Post by ajayk6 on 2011-06-04
Hi everyone,
I am a recent convert to Ubuntu 64 bit 11.04 with an ideal goal of promoting alternative OS environments and I am very impressed with the features it has for a free product. Now, I am having a few quirks I am having to deal with and I am hoping to find some solutions to those. I tried to do my due diligence by searching for solutions on this forum and on the web, but did not find solutions that worked. Granted I spent no more than 4 hrs on the search mission. I have three issues currently.

1. When I installed Ubuntu, I had the launcher and I really liked it.At some point either due to accidentally changing some settings or for an unknown reason I lost it. Now I cant figure out a way to get it back. I tried several things such as using the shortcut keys, compizconfig settings, dragging my mouse to the left, making sure I login as Ubuntu desktop as supposed to other options such as Ubuntu Classic etc,making sure I have the Unity plug in installed etc. Still cant find it. That gave me a thought on the potential future enhancement to Ubuntu. A Undo user setting feature, or a user setting history feature. Since Linux lets you customize so much, its very easy to get lost and unable to recover from some of the settings that were unintentional. This would be particularly helpful for beginners like me and may be help more people migrate to Linux.

2. The click and drag window feature of the Touchpad is a little annoying. When I left click and hold and then try to drag a window by sliding my other finger on the touch pad I am immediately presented with a menu listing to minimize and maximize. The window does not move. Granted Alt+f7 does let me drag windows but I am more used to using my touchpad on my laptop to do this task.

3. When I close the lid on my laptop and open it, the computer screen stays blank, though my power button indicates the computer woke up.In this case, I have to force a shut down. I suspect if this is an issue specific to my laptop as I have integrated graphics card and a nvidia graphics card. Not sure if thats causing the problem. I did have my ubuntu update completed already. So any missing drivers hopefully should have been updated?

Sorry about the long post. I tried to consolidate multiple issues into one rather than posting several. From what I hear, the linux forum experts go out of their way to help others. I greatly appreciate all your help.
Jay

---

### Post by steinerd on 2011-06-04
> **ajayk6 said:**
> Hi everyone,
I am a recent convert to Ubuntu 64 bit 11.04 with an ideal goal of promoting alternative OS environments and I am very impressed with the features it has for a free product. Now, I am having a few quirks I am having to deal with and I am hoping to find some solutions to those. I tried to do my due diligence by searching for solutions on this forum and on the web, but did not find solutions that worked. Granted I spent no more than 4 hrs on the search mission. I have three issues currently.

1. When I installed Ubuntu, I had the launcher and I really liked it.At some point either due to accidentally changing some settings or for an unknown reason I lost it. Now I cant figure out a way to get it back. I tried several things such as using the shortcut keys, compizconfig settings, dragging my mouse to the left, making sure I login as Ubuntu desktop as supposed to other options such as Ubuntu Classic etc,making sure I have the Unity plug in installed etc. Still cant find it. That gave me a thought on the potential future enhancement to Ubuntu. A Undo user setting feature, or a user setting history feature. Since Linux lets you customize so much, its very easy to get lost and unable to recover from some of the settings that were unintentional. This would be particularly helpful for beginners like me and may be help more people migrate to Linux.

Try hitting 
```
<ctrl><alt>+<f2> login to terminal session and type "unity --reset"
```or from GUI
```
 <alt>+<f2> unity --reset
```2. The click and drag window feature of the Touchpad is a little annoying. When I left click and hold and then try to drag a window by sliding my other finger on the touch pad I am immediately presented with a menu listing to minimize and maximize. The window does not move. Granted Alt+f7 does let me drag windows but I am more used to using my touchpad on my laptop to do this task.

I highlight the window decoration area and double-tap my touchpad then drag the window where ever I like.  no need to hold a key down.

3. When I close the lid on my laptop and open it, the computer screen stays blank, though my power button indicates the computer woke up.In this case, I have to force a shut down. I suspect if this is an issue specific to my laptop as I have integrated graphics card and a nvidia graphics card. Not sure if thats causing the problem. I did have my ubuntu update completed already. So any missing drivers hopefully should have been updated?

If your system is going into suspend or hybernate when you close the lid this could be the case.  mine was an ACPI problem.  not quite sure how to help with this one... I disabled the suspend and hibernate functions.

I have a site where I have consolidated some tips... maybe you can find more info there also.

[deep-sea.realservers.info]("http://deep-sea.realservers.info")

Sorry about the long post. I tried to consolidate multiple issues into one rather than posting several. From what I hear, the linux forum experts go out of their way to help others. I greatly appreciate all your help.
Jay

Hope I was able to help....

---

### Post by Copper Bezel on 2011-06-05
The last is probably a graphics card issue. I have a friend with a Toshiba laptop with a similar problem - basically, the graphics card doesn't wake up with the rest of the system on resume. Do you have the proprietary drivers installed?

---

### Post by ajayk6 on 2011-06-05
> **steinerd said:**
> Hope I was able to help....
1.The reset command did not work. Still cant see the Launcher. 
2. I could not figure out the touchpad instructions. What is a window decoration area. I double tapped my touchpad on the title bar of firefox, but it did not anchor my mouse to the window to be moved.
3. I think I can live with the closing the lid issue for now. It has to be a hardward issue and very specific to my situation. I will try to figure this out by myself.

Thanks.
Jay

---

