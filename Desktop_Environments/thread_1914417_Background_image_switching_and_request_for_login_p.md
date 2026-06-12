---
title: "Background image switching and request for login password on startup"
date: 2012-01-24
forum: Desktop Environments
---

### Post by crazybasenji on 2012-01-24
This all started when I added a wireless printer connection. I had previously been using a wired connection to satellite internet. Now when I turn on my computer and my desktop appears, I get the window asking for my login password, which never used to happen. I don't log out because I'm the only one who uses this laptop. Whether or not I type in my password, the desktop background image changes from my current one to one I used previously -- like, over a year ago -- and then changes back. This happens several times before it "settles" on one of the images. The first time it happened, I was away from the computer as it booted up and I came back to find a different background picture, none of my desktop icons except for a generic execute icon for Filezilla. Even my toolbar was gone. I had to right-click on the screen to open anything.

Now when I start my computer I sit and watch it, and when my normal desktop appears, I open my desktop settings screen. Sometimes at that point, the images stop playing musical chairs, but not always. Sometimes I still end up with the "alternate" background image, which I deleted from my pictures folder to no avail. I have managed to keep my toolbars visible with either background. 

I've tried: Changing my background to one of the "built-in" ones; I have gone to the Settings -> Xfce 4 Settings Manager to see if there was something I could change there in the Appearance, Desktop, or Display menus, but didn't see anything labeled "Make background hold still"(and the choices that are given don't seem relative -- I could be wrong about that). I've searched this forum and found other, similar issues, involving Gnome and KDE, and got the impression that incompatibilities can cause something like this. So maybe my laptop doesn't like the wireless network?

As a noob with anything related to terminal use, if you have any suggestions for fixing this that require using the terminal, please put them in the form: "type this, then type that, then hit enter." Or words to that effect. I would appreciate it very much.:)

---

### Post by crazybasenji on 2012-02-05
Apparently nobody else has had this same problem, but I managed to finally fix it. I thought maybe if I upgraded to a newer version of Xubuntu, so I now use Maverick. But that actually made the situation worse because the background would get "locked" on the wrong image -- the one without the working links to FileZilla and Thunderbird. 

I came back and started scanning forum posts for possible similar situations and found this: [http://ubuntuforums.org/showthread.php?t=1920149](http://ubuntuforums.org/showthread.php?t=1920149) which led to this: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce). And when I followed the directions for switching to pure xfce desktop, I no longer got the rogue background image. 

Maybe this will help someone else someday.

---

### Post by grahammechanical on 2012-02-05
Experiences like this one tell me not to mess with my working install. I have other partitions that I can install other editions of Ubuntu on for experimenting with.

I also think that it is better to do a clean install of something like Xubuntu or Edubuntu than installing the relative desktops of these editions on top of a standard Ubuntu. It is just too many variations of configuration scripts and libraries for things to work smoothly, in my opinion.

Regards.

---

### Post by crazybasenji on 2012-02-07
@grahammechanical -- I don't know enough to mess with much of anything, believe me. My Lucid Xubuntu was working fine until I added the wireless connection for the printer...which I didn't think would cause any havoc. Don't know why it did, just glad it's all better now. Thanks for the comment. :)

---

