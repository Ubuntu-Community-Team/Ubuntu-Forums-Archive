---
title: "Something broke in X"
date: 2009-08-27
forum: Desktop Environments
---

### Post by John Jason Jordan on 2009-08-27
I have Jaunty x86_64, nVidia Quadro 140M at 1680 x 1050 in Thinkpad T61. All updates are applied.

I have a slight handicap that makes a touchpad very difficult to use, so I have long used a bluetooth mouse. This morning it would not work, and this is the second time within a month. 

I have two bluetooth mice, a Razer ProClick Mobile and also a Logitech Travel mouse. 

If I do sudo hcitool scan it finds both mice just fine. If I do sudo hcitool cc <address> the command executes without error for either mouse. But the mice still do not work. Both mice work fine when I use them with another computer.

The last time this happened I figured that if bluetooth was working (it connects to my phone just fine), and neither mouse works, it must be a problem in X. I normally use the "nv" driver, so I did sudo nvidia-xconfig and restarted the computer. Switching to the nVidia driver cured the mouse problem. However, I don't care much for the nVidia driver, so I switched back to the "nv" driver by manually editing the xorg.conf file. That was a few weeks ago and the mouse continued to work fine with the "nv" driver - until just now.

So I tried the same fix again - that is, I switched to the nVidia driver and restarted the computer. But this time the mice still do not work. I also switched back the the "nv" driver, but again, no mousies.

I should also add that the desktop font has been messed up for the past several weeks. I have everything set to Sans 9 points in System > Preferences > Appearance. Text appears fine except that numerals appear in two different point sizes. As I write this the Gnome panel says it is "Thu Aug 27, 9:10 AM." The 9 is about one or two points smaller than the other numbers. But in other situations it is different numbers that are smaller, randomly. Also the line spacing is higher than it used to be, and when I enter text in dialog boxes as soon as I enter the first letter the line jumps down so the bottom half of the letters that I type are below the box.

There is one other symptom. For the past several weeks Firefox has been crashing a lot when clicking on a link. This includes links that always work fine, and when I restart Firefox and go to the link it works fine. Previously Firefox was always rock solid. Plus, I have had frequent lockups where the mouse and keyboard are dead, forcing me to use the power button. One time when this happened the caps lock light was flashing, but usually the computer is just locked up. There are no messages in /var/log/messages, and I get no error messages on screen. 

My conclusion is that something is broken in X. Unfortunately, I can't figure out what. I could use some troubleshooting suggestions. I really need my mouse back.

---

