---
title: "How to produce a screencast?"
date: 2005-07-27
forum: Desktop Environments
---

### Post by tag on 2005-07-27
I really would love to make a screencast, off of my desktop. Windows has it's Camtasia Studio, does anybody know about a good app for linux that can produce similar stuff?

---

### Post by mike998 on 2005-07-27
Gimp...
Also, the plain and simple "Print Screen" Key.

---

### Post by NeoChaosX on 2005-07-27
There's a "Take Screenshot" entry in the System menu. Simple as that.

---

### Post by smoon on 2005-07-27
I'm not exactly sure what you mean, but maybe [**Xvidcap**](http://xvidcap.sourceforge.net/), [**Wink**](http://www.debugmode.com/wink/) (It's freeware for Win and Linux) or [**vnc2swf**](http://www.unixuser.org/~euske/vnc2swf/) are what you're looking for.

---

### Post by spudley on 2005-07-27
On the screen shot topic, anyone know how to grab a screen shot of the login page??  

I modified a login 'theme' to suit my preferences, but the 'preview' graphic isn't accurate - I see other preview shots that show the login box, icons etc.  Mine isn't since I'm not logged in, I can't really get a screen shot.

Thanks!

---

### Post by smoon on 2005-07-28
[QUOTE=spudley]On the screen shot topic, anyone know how to grab a screen shot of the login page??  

I modified a login 'theme' to suit my preferences, but the 'preview' graphic isn't accurate - I see other preview shots that show the login box, icons etc.  Mine isn't since I'm not logged in, I can't really get a screen shot.

Thanks![/QUOTE]

Try to run gdm in Xnest:
```
gdmflexiserver --xnest
```
or
```
gdmthemetester console /path/to/theme/you/want/to/screenshot
```
should do the trick.

---

### Post by tag on 2005-07-29
I wasn't looking for a *screenshot* but a screencast - this is when pictues move, you know? :-)
@smoon - thanks for the tip, all three programs seem very promising, i will check them out some time soon.

---

### Post by tdaubs on 2005-12-06
I too am interested in any working solutions that people may have doing screencasts in Ubuntu.

---

### Post by bernardfrancois on 2006-03-03
There was a program called **istanbul** to do this. Check synaptic. I tried it but it didn't seem to work properly so I uninstalled it immediately. Maybe I wasn't patient enough.

---

### Post by Samhain13 on 2007-12-11
Hi, sorry for resurrecting such an old thread. But when I was about to make my own thread, this thread appeared as having a similar topic.

I just uploaded a video in YouTube. Here's the url: [http://www.youtube.com/watch?v=MFVuwV2gHs8](http://www.youtube.com/watch?v=MFVuwV2gHs8)

Video Description:

> 
Screencasting one of the many ways of making a screencast in Ubuntu.

The video is composed of small screen captures OGGs via GTKRecordMyDesktop and edited in Cinelerra. It shows The GIMP loaded with a composite of three paintings of Rembrandt, a Gnome-Terminal running FFMpeg2Theora, and the stock Ubuntu 7.10 desktop background image.

The music is called "Beyond Cairo", which I composed a couple of years back. It was written originally as a MIDI file using Cakewalk Pro Audio in Windows XP.


I'd appreciate your comments, suggestions and violent reactions (if any).

Cheers! :)

---

### Post by BCtom on 2007-12-12
Wow! I am very impressed. I always wanted to know how to do that. I used to do it the "other-way" using my TV/S-Video out, to capture my screencast, but this is truly amazing from my perspective. 

I like what you are able to with this! Very impressive. Oh, and cool music too!

The only thing I needed to do was, I had to change the name of GTKRecordMyDesktop, to just recordmydesktop because I guess they changed their name and moved the web site. Anyway, Synaptic loaded it up and in five minutes and I was capturing my screen for the first time without using any external devices.

Thank you Samhain13, et al, for your words. Another gold star for Ubuntu!

---

### Post by Lostincyberspace on 2007-12-12
There are quite a few programs in the repositories for screencasting found some while I was looking at window managers.

---

### Post by Samhain13 on 2007-12-12
BCTom: yeah, the capturing program is recordmydesktop. The gtkrecordmydesktop is the GUI for it. Sorry if I caused any confusion. And thanks for your kind words. Cheers! :)

[edit]
Ok, I just had to check so I know for sure if I've fed the wrong information. Just saw both recordmydesktop and the one with gtk- in Synaptic and the descriptions are as stated above. Additionally, I found out that KDE has its own GUI to recordmydesktop called, "krecordmydesktop".

Just wanted to follow up. :D

---

### Post by BCtom on 2007-12-12
Samhain13 --: This is sort of going off topic, but regarding your desktop.... What program(s) are you using to get that calendar and transparent System Display on your desktop? I know about the ciaro-clock, but the transparent system monitor looks interesting? Actually, your desktop looks very cool! Is that Berly?

Lostincyberspace --: Yeah, when I did a search for Window Managers, there they were.  Thanks. I see there are some options, and in different formats too!

I think I'm going to start a screen cast of my desktop very soon, you know, for prestige... ;-) LOL

---

### Post by MarilenCorciovei on 2007-12-16
Here is [a small article]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/screencasts-with-xvidcap/view") which shows how to use xvidcap and a custom flv player to make and display the screencast on the web. Maybe it helps.

---

### Post by Samhain13 on 2008-01-08
> **BCtom said:**
> Samhain13 --: This is sort of going off topic, but regarding your desktop.... What program(s) are you using to get that calendar and transparent System Display on your desktop? I know about the ciaro-clock, but the transparent system monitor looks interesting? Actually, your desktop looks very cool! Is that Berly?

Hello again, and thanks.

The calendar is from [Screenlets](http://www.screenlets.org), it's the default theme.

The transparent system monitor is called Conky. There's a few discussions regarding it here in the forums-- the discussions even have posts on the configuration files. I, however, just use the default configurations (except for a couple of colour changes).

And, I have CompizFusion (Advanced Desktop Effects in 7.10) enabled. But yeah, I used to use Beryl. :)

---

### Post by derrin on 2008-01-24
Thanks for the screencast!

I cannot get recordmydesktop to work on Gutsy.

I get:
recordMyDesktop has exited with status: 768
Description:Could not open/configure sound card
[IMG]http://thedevelopmentmanager.info/img_ref/recordmydesktop_error.png[/IMG]

Mic IS set to capture - so that is not the cause.
I have latest, updated version installed.

I have uninstalled and reinstalled.

I'm baffled.:confused:  

Can anyone out there help?

---

