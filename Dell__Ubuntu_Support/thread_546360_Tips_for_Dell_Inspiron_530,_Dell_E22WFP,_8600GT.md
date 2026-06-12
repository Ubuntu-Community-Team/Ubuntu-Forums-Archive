---
title: "Tips for Dell Inspiron 530, Dell E22WFP, 8600GT"
date: 2007-09-08
forum: Dell  Ubuntu Support
---

### Post by clarkburbidge on 2007-09-08
**1. Utilize The Real Estate!**

I wanted to get my fancy new Dell 22 inch LCD monitor working with better than the "out of the box" 12XX x 9XX resolution. I spent quite a bit of time before I ran across this great post.
[B][COLOR="Green"]
[How to Setup Dell E228WFP on Ubuntu 7.04, Inspiration 530]("http://ubuntuforums.org/showthread.php?p=3331568#post3331568")[/COLOR][/B]

**2. Fix The Graphics**

The nVidia 8600gt card was not working out just right. I really wanted to use Compiz, but wasn't getting it to work. I tried to use [COLOR="Green"]**[this tutorial]("http://www.robdian.co.uk/content/view/56/27/")**[/COLOR], but for some reason it didn't work for me. Probably a [PEBCAK]("http://http://en.wikipedia.org/wiki/Pebcak") or [ID 10 T]("http://en.wikipedia.org/wiki/ID-Ten-T_Error") error. I wish it had worked for me because his blog is super sweet looking, and the instructions were fantastic. You should go there just to admire and learn how blogs and how-to's should look. 

In the end I fired up the **[COLOR="Green"][ENVY]("http://albertomilone.com/nvidia_scripts1.html") [/COLOR]**installer. This was a breeze!

That and the combination of...
[B]
3. Fancy![/B]

... this [COLOR="Green"]**[excellent Compiz / Emerald how-to]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")**[/COLOR] (Same praise as above for this great looking blog and how-to!)

**4. Cincom Smalltalk Visual Works NC**

I was struggling getting this installed. For reasons explained better in this [COLOR="Green"]**[solution]("http://marc-abramowitz.com/archives/2006/10/09/the-trick-to-installing-cincom-smalltalk-on-ubuntu/")**[/COLOR], the net installer wasn't working. I had the same problem on my laptop so I think it is a software issue rather than a hardware one. 

On my laptop the install cd was recognized as containing an autorun component. No dice on my desktop. The cdrom mounted but all the files needed other permissions or mountings. Here is the error i was getting:
```
clark@dell:/media/cdrom$ sudo sh /media/cdrom/installUnix
exec: 45: /media/cdrom/vw7.5nc/bin/linux86/visual: Permission denied
The virtual machine for your platform:
    /media/cdrom/vw7.5nc/bin/linux86/visual
exists but cannot be executed.  The file system/CDROM containing
the virtual machine must provide execute permissions.
Please remount the file system/CDROM and try again.
clark@dell:/media/cdrom$ 

```

After following the instructions linked above I was ablt to use the Network Installer, but I 'd still like to know why:

It didn't autorun as it did on my laptop.
What all the permissions and remount stuff was about.

---

