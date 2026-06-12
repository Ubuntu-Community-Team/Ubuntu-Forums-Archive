---
title: "Disappearing wallpaper"
date: 2014-09-02
forum: Desktop Environments
---

### Post by Mike_Walsh on 2014-09-02
Evening, all.

Along with Ubuntu 'Trusty', I'm running a bunch of the other 'buntu distros.....including Lubuntu 14.04 LTS.

I've changed the default wallpaper to one of my own. However, every time I boot into Lubuntu, I find, when I reach the desktop, that my wallpaper has disappeared, leaving me with a black screen. (That's because my background colour is set to black.) My top panel, icons and bottom panel 'dock' are still showing. The wallpaper is still in the home folder, which is where I keep it; but it has to be re-applied each time I log in...

Am I making a mistake, in assuming I should keep the wallpaper file in my 'Home' folder? Because that's where I keep it, in Ubuntu.....and the wallpaper in Ubuntu ALWAYS shows up. The particular image file is still selected in Desktop Preferences; but I'm having to constantly re-select it every time. Or do I need to keep it in the same folder as the default wallpapers..?

Does anyone have an explanation for why this is happening? And does anybody have a work-around for this 'glitch' in Lubuntu?

(I know there are a few others recognised for this particular distro, but I've pretty well fixed most of them; this one's just plain 'bugging' me..!)

Any help or advice would be appreciated.


Regards,

Mike.

---

### Post by Rex Bouwense on 2014-09-02
Hi Mike,
Try looking here:
[https://help.ubuntu.com/community/Openbox#Wallpaper](https://help.ubuntu.com/community/Openbox#Wallpaper)

---

### Post by Dennis N on 2014-09-02
As a start, I would copy the disappearing wallpaper into the folder with the default set, select it from there, and see if this weird behavior continues. 

/usr/share/lubuntu/wallpapers

Also, if you select the original default wallpaper from this folder again, does it also disappear? I put all of mine in there, just to have them all together, and the selected wallpaper have never failed to show.  Not saying this will solve it, but it's one thing to be tried.

---

### Post by Mike_Walsh on 2014-09-03
Hi, guys. Thanks for showing an interest..!

@Rex; 

Haven't yet had a chance to look at the link (only just logged on), but will see what it says. I guess it may well be something to do with Openbox, it being the window manager. I suspect it may also be something to do with permissions.

(Have just made several attempts to open your link, in both Firefox AND Chrome; for some reason, it WILL not connect. Other community wikis will open.....just not that one!) Very strange!

*********************************************************************************************************

@ Dennis;

Copying the image into the default wallpapers folder was something I DID try last night.....but this is where my inexperience shows. I tried to change the permissions for the folder, from 'User only' to 'Anyone'; but I got a copy error in both cases. I'll admit, I don't fully understand how you change permissions in Linux.

To answer your question; having reset things to the default wallpaper, that shows up nicely upon login. So, I STILL think folder permissions is where I'm coming unstuck...

Regards,

Mike.

---

### Post by Dennis N on 2014-09-03
> **Mike_Walsh said:**
> 
@ Dennis;

Copying the image into the default wallpapers folder was something I DID try last night.....but this is where my inexperience shows. I tried to change the permissions for the folder, from 'User only' to 'Anyone'; but I got a copy error in both cases. I'll admit, I don't fully understand how you change permissions in Linux.

To answer your question; having reset things to the default wallpaper, that shows up nicely upon login. So, I STILL think folder permissions is where I'm coming unstuck...

Regards,

Mike.

It's a good sign that the default wallpaper is not doing this. Don't change the folder permissions. If anything you change the file permissions on the wallpaper files. Let's be sure they are all the same:

Here is my /usr/share/lubuntu/wallpapers:

```
dmn@Kayleigh:/usr/share/lubuntu/wallpapers$ ls -l
total 5476
-rw-r--r-- 1 root root 715819 Mar 12 10:44 1404-Arvore_by_Cleide_Isabel.jpg
-rw-r--r-- 1 root root 721999 Mar 12 10:44 1404-Copan02_by_Cleide_Isabel.jpg
-rw-r--r-- 1 root root 542401 Mar 12 10:44 1404-Daisie_by_Cleide_Isabel.jpg
-rw-r--r-- 1 root root 626912 Mar 12 10:44 1404-lubuntu-default-wallpaper.png
-rw-r--r-- 1 root root 700687 Mar 12 10:44 1404-Vale_by_Cleide_Isabel.jpg
-rw-r--r-- 1 root root 452176 Mar 12 10:44 1404-Vista_Do_Fitz_Roy_by_Cleide_Isabel.jpg
lrwxrwxrwx 1 root root     29 Aug 31 11:28 lubuntu-default-wallpaper.jpg -> lubuntu-default-wallpaper.png
lrwxrwxrwx 1 root root     34 Aug 31 11:28 lubuntu-default-wallpaper.png -> 1404-lubuntu-default-wallpaper.png
-rw-r--r-- 1 root root 208707 Aug 31 13:03 wallpaper-1526469.jpg
-rw-r--r-- 1 root root 805517 Aug 31 13:03 wallpaper-625827.jpg
-rw-r--r-- 1 root root 811790 Aug 31 13:03 wallpaper-990551.jpg

```

The three at the bottom were added by me. Your permissions should look like these*. The owner and group should be root. If the permissions of the one you added are different, you can change it's permissions to be the same as the others:

* there are two symbolic links in there with different permissions from the images - leave them alone.

first get to the wallpaper directory:
**[FONT=Courier New]cd /usr/share/lubuntu/wallpapers[/FONT]**
then, for any that do not start with **-rw-r--r--**
**[FONT=Courier New]sudo chmod 644 filename[/FONT]**
substitute the correct file name here. _Again, leave the symbolic links as they are_.

Also, I believe the wallpaper you use should be either a .jpg or a .png file.

For reference, the wallpapers folder has these permissions (numeric code 755):
```
drwxr-xr-x 2 root root 4096 Aug 31 13:03 wallpapers

```

---

### Post by Mike_Walsh on 2014-09-03
Hi, Dennis.

Hm! Well, now; I've tried accessing the wallpapers folder via the terminal, with a singular lack of success...

The problem I have at the moment is that I can't get the /usr/share/lubuntu/wallpapers folder to even accept the file transfer when I attempt to copy my image into it. This is what I'm getting every time:-

[ATTACH=CONFIG]256096[/ATTACH]

And this is how permissions currently are for the image I want to add to the folder:-

[ATTACH=CONFIG]256099[/ATTACH]

I've stretched the error message window so you can see it. I'll be frank, I'm still at the stage where I'm more at home with a GUI than with the CLI; I haven't yet reached the 'pipe and comfy old slippers' stage, I'm afraid..!! I must admit, though, that even to me, that 'Nobody' for the execute permissions doesn't look quite right, somehow!

Regards,

Mike.

---

### Post by Enigma12 on 2014-09-03
Mike, I was having the same problem of my chosen wallpaper not reappearing after shutting down and restarting. I found the answer given to someone else by bapoumba (sp?). Thank you, nice lady, for solving this for the OP and me and possibly others.

Put the wallpaper file in your Pictures folder. That folder was created automatically when I first loaded Lubuntu. I have 136 different photos in that folder and change both desktops daily. Every day the previous day's wallpapers display and I just choose whichever other ones I prefer for that day. It's one of the **many** reasons I settled on Lubuntu and stick with it. 

If it works for you as well as it works for me, I will rejoice about FINALLY being able to help someone.

---

### Post by Dennis N on 2014-09-03
Well, the permissions on the file aren't what they should be. Change **View Content** to **Anyone** and see if that fixes things without doing anything more like moving the file. 

I really hope that solves it. If not, continue on and be careful. You also have the suggestion in the post just above to consider.

If you want to use the file manager to copy (or move) the file, you have to open the file manager with root permissions, because only a user with root permissions can copy a file to that wallpaper folder. For that, you open the terminal and type:

[B][FONT=Courier New]gksu pcmanfm

[/FONT][/B](an icon will appear on the tool bar at the left to indicate that pcmanfm is running with root permissions.)

When you are done copying, close the file manager to end the root session. Otherwise you can inadvertently cause havoc if you continue in that mode.

---

### Post by Mike_Walsh on 2014-09-03
Thanks for your reply, Wayne.

I'm currently in the middle of doing my first major backup in Ubuntu! As soon as I get a chance, I'll give your suggestion a try.

I suspect, thinking about it, that it may well work. It's similar to the problem I had in Kubuntu, of finding the correct location for personal custom wallpapers that aren't part of the default set. I posted a query about that, a few weeks ago; and the answer in that particular case, turned out to be the Pictures folder too...

I'm still pretty new to Linux myself; been on the forums about the same time as you. Like you, I've been able to help a couple of people already, but it's small 'payback' for the reams of good advice I've already received! My bean count might be five times yours, but that just shows I'm a chatty so-and-so...

One of my interests is graphic design, and has been for many years. To this end, I use ONE Windows program under Wine that I just haven't been able to find an equivalent for in Linux. It's PhotoScape v3.6.5, running under Wine 1.7.2; a combination that fortunately has the coveted 'platinum' rating, meaning that it works perfectly!

I like to custom design my own wallpapers; usually involving abstract images, with distro-themed text and graphics superimposed over the top.....a pastime that affords me endless hours of great pleasure.

I'll get back to you shortly, when the backup's run its course, and let you know how I get on.


Best regards,

Mike.

---

### Post by Mike_Walsh on 2014-09-03
Thanks for getting back to me, Dennis. 

I am going to try Wayne's suggestion, as soon as this backup's run its course. If that doesn't work, I'll have a try at your suggestion!

I think Wayne's 'tweak' might do the trick; simply because it's very similar to the problem I had with wallpapers in Kubuntu (the Plasma desktop is a very different beast to most of the other 'buntus!) My 'blind spot', I suspect, is in thinking that because things work one way in Ubuntu, that they're going to work the same way with its offspring!

The Home folder is definitely the place for wallpapers in Ubuntu; I'm already discovering that the others DO have their own quirks and peculiarities, enough so that I can understand why people very often prefer one distro to another...

Will let you know how I get on. This is what I like about these forums; everybody on here is just so helpful..!

Regards,

Mike.

BTW, thanks for the tip about running the file manager with root permissions. Yet another 'nugget' of info I will, no doubt, make good use of over the coming years, 'cos I'm NEVER going back to Windows, that's for sure!!

---

### Post by Mike_Walsh on 2014-09-03
> **Dennis N said:**
> If you want to use the file manager to copy (or move) the file, you have to open the file manager with root permissions, because only a user with root permissions can copy a file to that wallpaper folder. For that, you open the terminal and type:

[B][FONT=Courier New]gksu pcmanfm

[/FONT][/B](a key icon will appear on the tool bar at the left to indicate that pcmanfm is running with root permissions.)

When you are done copying, close the file manager to end the root session. Otherwise you can inadvertently cause havoc if you continue in that mode.

Dennis; you're a gent..!

Your suggestion to copy the image into the wallpapers folder in root mode worked a treat. It's now sorted, and both logout/login AND reboot bring the wallpaper up every time.

I did try your first suggestion, but I didn't have too much faith that it would fix it; it didn't. Never mind; it's sorted now, and the desired result has been achieved, together with a little bit more knowledge gained along the way.....nice one!

***************************************************************************************

@Wayne;

I DID give your suggestion a try, don't think I didn't. I had more faith in trying it your way initially, simply because it's a much simpler fix. I'm ALL for doing things the easy way!

I've tried a few other suggestions from different people over the last few months, to do with various aspects of my other distros. Sometimes they work, sometimes they don't. Don't feel TOO badly about it. I believe a lot of the reason for this is the fact that no two individuals run precisely the same combination of hardware/software, with the end result that there's a lot of variables with regard to the different configuration files, modules, libraries, scripts, etc., that we end up with. I truly believe that this pretty much gives every 'puter running Linux, in whatever shape or form, a 'personality' as individual as a fingerprint.

I'm sure that as both of us gain more experience with our systems, we will in our turn be able to help other people with our hard-won knowledge..!

BTW; I thought you might both like to see the image that's been giving me such a headache! Here it is 'in situ', along with my bottom 'dock':-

[ATTACH=CONFIG]256112[/ATTACH]

Thanks, guys.

Regards,

Mike.

*I'll mark this as 'Solved'.....sorted!*

---

### Post by Dennis N on 2014-09-03
Hey Mike - 
Glad to hear it worked!

---

### Post by vasa1 on 2014-09-04
> **Mike_Walsh said:**
> ...
BTW; I thought you might both like to see the image that's been giving me such a headache! Here it is 'in situ', along with my bottom 'dock':-
...
If you don't mind my asking, what is the indicator just to the left of GB in the top panel?

---

### Post by Mike_Walsh on 2014-09-04
Hello, vasa.

Quite simple. It's the CPU usage monitor. 

Right-click your main panel (I don't know where you have yours, but I moved mine to the top to make way for a 'dock' at the bottom); Panel Settings>Panel Applets>Add, then scroll through the available list until you find 'CPU Usage Monitor'. Click 'Add', then just position it where you want it with the 'Up' and 'Down' arrows.

Simples..!

I also have PSensor installed (that's the little thermometer symbol between the keyboard layout handler and network applets); it's essentially been written FOR Ubuntu, but I find it works to a greater or lesser degree in most of the 'buntus. It has an 'experimental' feature, which allows you to place which of the various sensor readouts you want into the panel beside the symbol; it works perfectly in Ubuntu, Xubuntu, & Zorin. Kubuntu doesn't need it, as it has its own set of System monitoring tools in the panel 'Widgets' section. In Lubuntu, you can't get the readouts into the panel, but you can still bring up the monitoring info and history graphs by left-clicking, so it's no biggie.

In case you're interested, have a look at this link. The repository IS perfectly safe.....I've been using it for quite a while:-

[http://www.webupd8.org/2014/06/psensor-updated-with-option-to-display.html](http://www.webupd8.org/2014/06/psensor-updated-with-option-to-display.html)

PSensor IS in the main repositories; it is, however, an older version without the 'experimental' feature.

Regards,

Mike.

---

### Post by vasa1 on 2014-09-04
Mike, thanks for the detailed response. I used both CPU monitor and PSensor in the past. But I'm constantly on the lookout for something "lighter". So now [I'm using Conky]("http://ubuntuforums.org/showthread.php?t=2242484") to provide me with (nearly) the same information.

The reason I asked was that I *thought* it was the CPU monitor but wasn't sure: I noticed it because the CPU usage in the image seemed quite high for quite sometime. Because I use a laptop, I keep a lookout for both CPU temp & usage to avoid a puddle of molten computer ;)

---

### Post by Mike_Walsh on 2014-09-04
I know what you mean!

I'm using a 10-yr old Compaq Presario desktop these days. It's ancient by today's standards, but in its day it was 'high-spec'; and it has the saving grace of that Athlon 64 (brilliant CPU!) I've trebled the RAM to 3 Gb, too...but I'm limited by virtue of using DDR1.

I switched to Linux back at the tail end of May; before that, when running XP, I used HWMonitor, and Speccy. I'm not a beginner, as I've been playing around with these things for about 35 years. I used to run an ancient Dell laptop, an Inspiron 1100, with the 'Netburst' Intel Celeron. That thing used to regularly pull temperatures of 80C+.....frightened the life out of me, until I found out that ALL Intels of that vintage used to run just as hot..!

I still have the Dell. It's now running Puppy 'Slacko'.....and it runs round about the 40C mark; half of what it was when it, too, ran XP. Go figure..!

The Compaq averages 28-30C. I've also just removed, cleaned out and re-seated the cooler for probably the first time in it's life. The temps have now dropped a further 2-3 degrees...

BTW, the readout was high because I had Skype running in the background...it ALWAYS seems to do that, no matter which OS I happen to be using.

Better stop there; I'm wandering WAY off-topic here; I'll end up in the Jail if I'm not careful!

Regards,

Mike.

---

### Post by vasa1 on 2014-09-04
> **Mike_Walsh said:**
> ... BTW, the readout was high because I had Skype running in the background...it ALWAYS seems to do that, no matter which OS I happen to be using.
...
Aha! That explains why I didn't see anything "significant" running which could easily explain the high CPU usage.
And [this is what Alice does]("http://www.dilbert.com/dyn/str_strip/000000000/00000000/0000000/200000/00000/2000/200/202254/202254.strip.print.gif") for Skype.

---

### Post by Mike_Walsh on 2014-09-04
Oh YES, indeedy...!

It's a sod to shut down when you've enabled the auto-start function by mistake...

Regards,

Mike.

---

### Post by J Tinsby on 2014-09-04
Mike and the rest,

You are all miles ahead of me. I don't see anything in my /home folder even after using Ctrl+h that resembles a .jpg or.png file of wallpaper. Yes I can see the photos when I choose the settings | appearance but beyond that I haven't a clue how to find the actual file in ubuntu! I found an .xml file that references the one in use but that's all. I even tried, with no success to run the command:

> **[FONT=Courier New]cd /usr/share/ubuntu/wallpapers[/FONT]**

Of course no joy there either, tough to understand why some simple things are so hard to locate. I installed some nice wallpaper from an earlier version of Ubuntu called Oneiric but I can't find it anywhere. Yes I can use it but locating it is another story. 

Thanks,

J T

---

### Post by Mike_Walsh on 2014-09-22
> **J Tinsby said:**
> Mike and the rest,

You are all miles ahead of me. I don't see anything in my /home folder even after using Ctrl+h that resembles a .jpg or.png file of wallpaper. Yes I can see the photos when I choose the settings | appearance but beyond that I haven't a clue how to find the actual file in ubuntu! I found an .xml file that references the one in use but that's all. I even tried, with no success to run the command:



Of course no joy there either, tough to understand why some simple things are so hard to locate. I installed some nice wallpaper from an earlier version of Ubuntu called Oneiric but I can't find it anywhere. Yes I can use it but locating it is another story. 

Thanks,

J T

Hi, JT. Sorry to be a while getting back to you....had a lot of 'irons in the fire' this last coupla weeks..!

I'm not REALLY 'miles ahead of you'. I've just spent the last 30-odd years playing around with these things, that's all; and I've always found this sort of thing very easy to grasp the basics of! I'm going back to the days of the Commodore 64, Sinclair ZX81, and the infamous Tandy TRS-80 (the 'Trash 80', as some people fondly called it (!)

That's quite a simple one. You're almost on the right track, actually. Simply go into Pcmanfm; and at the top of the main window (not the sidebar), there's a big search box. If you type

 > /usr/share/lubuntu/wallpapers

into that box, and hit the search icon at the far right, your wallpapers will come up. Simples...!

It won't appear if you type it into the terminal. I'm not yet quite sure what that DOES do, but it won't produce the result you're after.


Regards,

Mike.


**EDIT: **I just realised; you said Ubuntu, not Lubuntu, didn't you? I'm not sure where they are in Ubuntu; never actually looked for them in Nautilus, and the layout's somewhat different, too. Usually, I save wallpapers to my external Seagate HDD, then, when I want them, I copy to the 'Home' folder. I then click on the image I want to use; it comes up in 'Image Viewer'; I right-click on the image in the viewer, and you get the option to 'Set as Wallpaper'....that's how I do it.

I don't believe Ubuntu actually HAS a 'Wallpapers' folder, now I think about it. When you install, you've simply got the default one, and I think that's it... Doesn't really matter if it has, anyhow. Installing personal custom wallpapers is just about the first thing I do on any system (after applying all available updates, of course!)

Hope that helps.

Mike.

---

