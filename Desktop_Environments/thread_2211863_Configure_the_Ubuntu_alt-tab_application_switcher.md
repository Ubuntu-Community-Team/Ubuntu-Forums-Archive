---
title: "Configure the Ubuntu alt-tab application switcher"
date: 2014-03-18
forum: Desktop Environments
---

### Post by Tomas_Gustavsson on 2014-03-18
I always struggle with this when installing a new version of Ubuntu, so I thought I'd post it here so I can find it myself easier next time :-)

I am currently on Ubuntu (Unity) 14.04 Trusty Tahr, but I was doing the same in 13.10 and 13.04.

I simply don't like the default Unity alt-tab application switcher. It may work for a lot of people, but it just slows me down. For me it's faster to have a single application switcher that cycles through all open windows, possibly withing one desktop, but I'm not sure about that. 
I am really not compatible with the default unity switcher that groups windows, for example terminals, together so when hitting alt-tab you can't (in an effective way) switch between terminals. Having a different key combo for that slows my brain down.

I realize other peoples preferences varies, that's why this post is so great, it shows you how to tweak it the way you want it (other switchers have a lot more options than the unity default one).

So anyhow on to how to change the alt-tab application switcher in ubuntu unity.

sudo apt-get install compizconfig-settings-manager
sudo apt-get install compiz-plugins

Open compizconfig-settings-manager with alt-F2, type ccsm.

Scroll down to "Ubuntu Unity Plugin". Choose the tab "Switcher". Disable the alt-tab and shift-alt-tab key bindings. ("Key to start the switcher" and "Key to switch to the previous window in the Switcher".
Click the "Back" button.

Scroll down to the "Window management" section. Here you can select another switcher.
I enable the "Static Application Switcher", resolve any potential conflicts by setting the setting for "Static Application Switcher". 
Now you can tweak the switcher by clicking on it. I have changed alt-tab and shift-alt-tab to "Next window (All windows)" and "Prev window (All windows)". 

Experiment to find the settings that work best for you. It you want to go back to the poriginal settings, simply disable the Static Application Switcher and enable the key bindings in "Ubuntu Unity Plugin" again.

Hope someone find this helpful.

---

### Post by Samhain13 on 2014-04-27
Thank you!

---

### Post by craig10 on 2014-06-13
> **Tomas_Gustavsson said:**
> Scroll down to the "Window management" section. Here you can select another switcher.

Weird. I don't see an option to choose a new switcher. I only see six options:


[LIST]
[*]Grid 
[*]Move Window 
[*]Place Windows 
[*]Resize Window 
[*]Scale 
[*]Snapping Windows 
[/LIST]

Am I missing something? I'd really like to get rid of the infuriating grouping of windows.

---

### Post by craig10 on 2014-06-13
Damn, I just realised that this thread is marked as solved, so I suppose I should start a new thread.

---

### Post by dctech1000 on 2014-07-06
Thank you ! This worked great - I was tearing my hair out !

---

### Post by david-9ei9nyjpwdexg on 2014-09-04
Thanks! This helped immensley. The upgrade removed the compiz-plugins package, which includes the application switcher, so all of my ubuntu machines lost the ability to alt-tab after upgrading.

---

### Post by eddieshowcase on 2014-09-30
I ran into this same issue.... and I needed to install via synaptic the "compiz-plugins" package as well.


> **craig10 said:**
> Weird. I don't see an option to choose a new switcher. I only see six options:


[LIST]
[*]Grid 
[*]Move Window 
[*]Place Windows 
[*]Resize Window 
[*]Scale 
[*]Snapping Windows 
[/LIST]

Am I missing something? I'd really like to get rid of the infuriating grouping of windows.

---

### Post by cloudwalker2 on 2014-10-20
Yes! Very helpful! Thank you!!

---

### Post by anacletus2 on 2014-10-20
Very helpful, I couldn't find an easy way to switch form one terminal to another since gnome!

Thank you!

---

### Post by nealmcb on 2015-01-13
Thanks - this is more clear and up-to-date than the askubuntu answer at [http://askubuntu.com/a/68171/6130](http://askubuntu.com/a/68171/6130)
Besides what you did, I also find it very helpful to go to the "Appearance" tab on the Static Application Switcher window in ccsm, click on "Selected Window Highlight" to show the sub-items there, click on the options by "Highlight Mode", and add "Bring Selected to Front".
Then as you switch you can see each whole window, in its actual location on the display, and thus be sure to select the right one.

Unfortunately, the Static Application Switcher suffers from Bug #1282900 &#8220;compiz static window switcher no longer displaying...&#8221; : Bugs : compiz package : Ubuntu
  [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1282900](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1282900)

---

### Post by emagar on 2015-03-27
Great! quite clear and very useful to remove a default that I found annoying. Kudos!
Now another question (I hope I can articulate it): Has anyone managed, with ccsm, to have "Show Desktop" included in the alt+tab application switcher loop? Using the ctrl+super+d "minimize all" gets you to the desktop, but then alt+tab will not return to the application-switching loop.

---

### Post by alito-organicrobot on 2015-05-09
I don't think this works on 15.04. Changing to any of the other app switchers and pressing alt-tab crashes unity.

---

### Post by firecentaur on 2015-06-05
THANKYOU SO MUCH!!!

I have been using ubuntu for a year now, and this was a MAJOR annoyance for me!

---

### Post by Copper Bezel on 2015-06-05
> **alito-organicrobot said:**
> I don't think this works on 15.04. Changing to any of the other app switchers and pressing alt-tab crashes unity.
It shouldn't. I get the same behavior in 15.04 as always from the Ring Switcher (which I've been using uninterrupted since ~2009.) Unassign Unity's Alt+Tab, activate the plugin you want, set bindings as you please, and it should work.

---

### Post by frieder-bluemle on 2015-08-18
This works like a charm on 15.04 - The alternative switcher is so much faster and less confusing. Thanks!!

---

### Post by joyehsu on 2015-09-09
Solved my problem, 14.04 LTS, thanks!

---

### Post by koelsch on 2016-03-29
I have the same problem, but none of the suggestions work for my system -- PLEASE help, it is driving me mad that I cannot switch with one hand between applications! (and Alt-Esc does not help much because with many applications and windows open it slows you down if you do not see the icons and thus cannot look ahead...). 

Just to be confirm: 
In the CompizConfig Settings Manager I have deactivated all switchers in the Unity Plugin and unchecked all boxes under the Switcher tab. (Ubuntu Unity Plugin is still enabled) 
In the Application Switcher (under keyboard, not mouse...) I have entered under Next window (All windows) <Alt>Tab 
and under Prev window (All windows) <Shift><Alt>Tab 

I run 
gnome-session 3.9.90
with 
unity 7.2.6
in ubuntu 14.04 LTS 
on a lenovo X1 Carbon 

/etc/default/keyboard shows: 
XKBMODEL="pc105"
XKBLAYOUT="de"

What is wrong here? 
HOW can I just switch between all application windows? 
ANY help will be greatly appreciated!!!

---

### Post by sam_singh on 2016-03-29
i tried and it works smoothly on [COLOR=#000000]15.04 .... Thanks buddy.. [/COLOR]

---

### Post by peter-a-klausner on 2016-06-16
On Ubuntu 16.04 LTS the ccsm does not sport a Ubunty Unity Plugin section (bug or feature?).  You still get the "Static Application Switcher" but I somehow failed to let that override the Unity settings.  The work-around:

sudo   apt-get install unity-tweak-tools

This gives you a tab with Unity switcher settings where you can disable <alt><tab> etc.

---

### Post by heiko-klein-j on 2016-07-05
Exactly what I needed, thanks.

---

### Post by n1k31t4 on 2017-03-29
Using Ubuntu 16.04 LTS, I have managed to find all the settings originally posted. See attached screen-shot to find the link to the Ubuntu Unity Plugin.

[ATTACH=CONFIG]274348[/ATTACH]

[screenshot is difficult to read from, as it is compressed too much through the upload process]


After opening `compizconfig-settings-manager`, go to the Desktop tab and there is a link there to the Ubuntu Unity Plugin.

---

