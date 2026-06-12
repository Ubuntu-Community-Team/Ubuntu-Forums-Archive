---
title: "Sound and Video Issues On New 1420n"
date: 2007-10-01
forum: Dell  Ubuntu Support
---

### Post by pingback on 2007-10-01
A week ago I got a Dell Inspiron 1420n laptop with Feisty Fawn pre-installed. I installed all of the updates in the update manager and have not made any changes to the system, but I am still having video and sound issues.

Here are the part IDs on the laptop:

Video Card: 

320-5495 Intel Integrated Graphics Media Accelerator 3100 Inspiron 1420

Sound Card: 

313-4783	Integrated High Definition Audio 2.0


The video issue I am having is with the desktop effects and OpenGL apps. What happens is if I have the desktop effects turned on and then I open an app that is running OpenGL such as 'glxgears,' when I move the app's window around, a static image of the last frame that app was on remains on the screen, until I move another window over it or refresh it. BTW, 'glxgears' is reporting 1000+ FPS. This occurs when I simply have the 'Desktop Effects' enabled in the 'Preferences' menu, but it also occurs if I am using Beryl.

The sound issue I am having is with games in addition to certain Flash apps I have running in Firefox. For games and certain flash apps, the sound is distorted. The sound is fine for YouTube, but not a certain flash app that is for videoconferencing. In that app, when someone speaks, their voice is very low pitch. In games the distortion is hard to describe, but it is definitely distorted.

I've searched the forums for any mention of this, but have not seen anything. BTW, I'm fairly new to Ubuntu and Linux. I know some of the commands, but am pretty much clueless as to what is going on under the hood with video cards and what not.

Thanks for your help.

---

### Post by pingback on 2007-10-11
No one has anything to say about this? So much for Ubuntu Dell 'support.'

---

### Post by oddabe19 on 2007-10-13
Sometimes patience is a virtue.  It might take awhile for someone to answer your post. There are millions of linux users and thousands that use this site.

As for flash issues, I do know that flash is not supported well in linux.  There have been many reports of problems with sound in the past (outside of Dell laptops).  The flash guys fail all the time with releasing a working version for linux.  Till then, try Gnash ```
sudo apt-get install gnash gnash-mozilla-plugin (or something like that)
``` and see how that works.

There are also some issues mentioned about video card and sound on Dell's Linux Wiki, which is a very useful site.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Known_Issues]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Known_Issues")

for what it's worth, my dell 1420n has been flawless after doing a little google research, and following a lot of steps on that Dell Wiki.

Hope this helped :-)

---

### Post by doppis on 2007-11-02
Try this for the video.

[http://ubuntuforums.org/showthread.php?t=506744&highlight=x3100](http://ubuntuforums.org/showthread.php?t=506744&highlight=x3100)

---

