---
title: "Linux runs Firefox (plus video and flash) much slower than Windows XP"
date: 2009-03-01
forum: Desktop Environments
---

### Post by teel on 2009-03-01
Hi there,
The topic may seem provocative but I am not tending to do it ;) I've been using Linux since 10 years and I've always claimed desktop environments are not as fast as Windows one, anyway always prefered Linux over Windows ;)

What especially drives me crazy is the speed of Firefox, all versions, all variants of *buntu, KDE, Gnome, XFCe. Flash uses 50% of my CPU, fullscreen youtube videos are just 10fps and 90% of CPU, Firefox holds user action when reading more complex websites, zooming in/out is way to slower than on Windows.
Athlon 2000XP 1.66GHz, 1GB RAM, nForce2 chipset, ATI Radeon X800, ATI proprietary drivers installed (no compiz). Windows XP works really good, Linux is unfortunately significantly slower in terms of desktop interface and web browser (Firefox, Konqueror, Opera) usage :(

Can anyone tell me what may be wrong? Does anyone have the same observations?

Best regards,
teel

---

### Post by kelvin spratt on 2009-03-01
My cpu runs at about 20% running flash with firefox with compiz running with full bells and whisttles and downloading at the same time. I would suspect its your graphics card pulling down your processor. A lot of graphic cards really don't work well with linux I now use a Nvidia with 510mb of internal ram and those glxgears run at 4,900 fps without compiz and 3,900fps  my old Ati card ran at 1,400fps without and 600fps with, and stole a lot of cpu youtube was crap now runs in fulscreen with no problems.

---

### Post by thtrgremlin on 2009-03-01
I'll agree with Kelvin. ATI Radeon X800 is most likely the culprit 1) Ati in general with regard to their Linux support and 2) not a particularly high performance card.

Just as an option, sadly, I've heard you can get better performance from Firefox installing the windows version with Wine. Worth a shot.

[http://tech.slashdot.org/article.pl?sid=09/02/13/0058251]("http://tech.slashdot.org/article.pl?sid=09/02/13/0058251")

---

### Post by benerivo on 2009-03-01
There's nothing wrong with linux, but firefox and flash are designed for windows performance (due to market share). See here for another [firefox]("http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox") comparison.

This is just the way it is. I'd beware of browser tests, as they usually  rely on javascript performance only, which isn't a comprehensive reflection of web browsing, and anyway the practical difference is very small.

---

### Post by skunkbad on 2009-03-01
I actually see Ubuntu being faster than Windows XP in regards to FF and Flash. I think it may be due to NOD32 AV on Windows. My computer is really fast though, so that may be why I have a different experience.

---

### Post by Yashiro on 2009-03-02
Linux is slower on the desktop. From browsing to video display it is all slower. It's more stable, usually, but it is indeed slower than XP at most mundane daily tasks.

---

### Post by teel on 2009-03-02
> **Yashiro said:**
> Linux is slower on the desktop. From browsing to video display it is all slower. It's more stable, usually, but it is indeed slower than XP at most mundane daily tasks.

What an unusual statement ;) From what I've heard I am the unlucky person who always buy "this wrong" hardware. Why then 99% of Linux users claim Linux is faster than XP? I agree in terms of heavy calculation like movie reprocessing, but for desktop it is way too slower than Windows

---

### Post by binbash on 2009-03-02
> **teel said:**
> What an unusual statement ;) From what I've heard I am the unlucky person who always buy "this wrong" hardware. Why then 99% of Linux users claim Linux is faster than XP? I agree in terms of heavy calculation like movie reprocessing, but for desktop it is way too slower than Windows

No one claims that, they claim it is faster after 6 months of usage  :)

---

### Post by eldragon on 2009-03-02
> **teel said:**
> What an unusual statement ;) From what I've heard I am the unlucky person who always buy "this wrong" hardware. Why then 99% of Linux users claim Linux is faster than XP? I agree in terms of heavy calculation like movie reprocessing, but for desktop it is way too slower than Windows

considering the other poster has a rather new computer (reading his hardware), id say you are down to the money, you are definately not alone here with web performance. there is something here slowing down.

the other user claiming java/flash benchmarks dont count for websurfing experience, how wrong can you be, websurfing is turning only into viewing/running java/flash.

imo, id say firefox is the problem, your x800 should be more than enough for that kind of content.

ive got intel drivers and suffer from the same issue. ive learned to live with it, until firefox's new java engine ships. well see what happens there.

---

### Post by teel on 2009-03-02
The problem is not only the Firefox. Wherever I run youtube it consumes lots more resources than Windows. I guess it's all environment working slower, e.g the Nautilus. But I would also suspect font and graphics rendering procedures in GTK.

I've tried different variants, even Swiftfox which is HW-optimised runs slower. I guess I will run FF via Wine.

---

### Post by eldragon on 2009-03-02
> **teel said:**
> The problem is not only the Firefox. Wherever I run youtube it consumes lots more resources than Windows. I guess it's all environment working slower, e.g the Nautilus. But I would also suspect font and graphics rendering procedures in GTK.

I've tried different variants, even Swiftfox which is HW-optimised runs slower. I guess I will run FF via Wine.

i dont understand this, you ran youtube...where?

anyway videos runs ok here, its flash/java's performace that sucks here.

---

### Post by chanyunkwan on 2009-03-02
firefox3.1 beta2 works much faster than before.

---

### Post by eldragon on 2009-03-02
> **chanyunkwan said:**
> firefox3.1 beta2 works much faster than before.

yes it does. still behind though..

---

### Post by teel on 2009-03-02
> **eldragon said:**
> i dont understand this, you ran youtube...where?

anyway videos runs ok here, its flash/java's performace that sucks here.

I browse youtube on Firefox, Opera, Konqueror, Epiphany etc. On each browser the speed of fullscreen video sucks.

---

### Post by eldragon on 2009-03-02
> **teel said:**
> I browse youtube on Firefox, Opera, Konqueror, Epiphany etc. On each browser the speed of fullscreen video sucks.

well, its all down to flash, the rendering engine is the same in all browsers...

download the .flv files somehow and use mplayer to play them, you will see it works ok there.

---

### Post by thtrgremlin on 2009-03-02
Hmm... guess I could make that comparison about speed. Never had windows on my newer machine, but personally, opengl desktop is quite fast with a good 3d card. Firefox may be a bit slower on ubuntu comparing 1 tab, but I have noticed when you got multiple windows and multiple tabs across several work spaces that the computer doesn't get progressively slower the more stuff you have open. Performance on Ubuntu seems to be much less effected by what other applications you have running at the same time. It is perfectly fine to let the computer run for months without restarting. It is always just as fast as when you first installed.

The thing that always drove me crazy with windows was how 1) every error is fatal and requires a restart 2) most updates require a restart 3) memory leaks can only be solved with a restart 4) Computer gets slower over time for no apparent reason. 5) Worlds most useless errors.

That was such a hard habit to break coming to Linux, reading error messages because they actually provided real, useful information that often leave you one google search away from a solution.

The things I love about Gnu/Linux are a world apart and have no comparison to Windows. When I am not satisfied with performance of anything, I tweak with it. Results are measurable and verifiable. It isn't just some box with things you click on to do the things the guy at the store told you it could do.

Linux turns your computer into a tool. It lets you do the kinds of things scientists and researchers do with computers. Windows is just a really really bloated console that let you kinds do things you have heard people can do with computers.

---

### Post by eldragon on 2009-03-02
> **thtrgremlin said:**
> 
The things I love about Gnu/Linux are a world apart and have no comparison to Windows. When I am not satisfied with performance of anything, I tweak with it. 

so how did you tweak flash ?

---

### Post by thtrgremlin on 2009-03-02
Personally, haven't had any issues with flash. I have no problems with the proprietary driver... but I have noticed that performance slows if you leave flash running. The best thing to do is just open a new tab and close the old one every once in awhile so no flash is running, then go back to what you were doing.

Well, that is if you want to use firefox with flash.

I get the very best media performance using a shell script I wrote that uses zenity to prompt for what I am looking for, then transcodes the video in real time and pipes it to mplayer with a few special options that makes it look better. It also allows videos to be played full screen, smoother, and you don't get that stupid, monstrous progress bar across the bottom of the screen. Know whats really ironic? it takes less time to buffer the transcoding process to start playing than it does to load all the advertisements on youtube.

Ok, while I wouldn't consider that "normal" tweaking... it is fun, and one of the reasons why I LOVE Gnu/Linux.

Have you tried any of the free flash alternatives such as gnash? I haven't tried it in quote awhile, but many of their tools are superior for users. When I did use it, it was better when it did work... and frequently didn't work on a site by site basis.

---

### Post by benerivo on 2009-03-02
> **thtrgremlin said:**
> ...Have you tried any of the free flash alternatives such as gnash?...

I've used the swfdec plugin recently (0.8.2-1) and it seemed to be the best alternative for me, although some sites wouldn't work with it. You can set it to not autoplay by default, which is useful if you want to open a few youtube tabs and not have them all start playing. I haven't really got a problem with adobe's flash as it works okay on linux. I don't really use flash in my web browsing, other than when i specifically want to watch a video clip.

---

### Post by Locutus_of_Borg on 2009-03-02
if you can spare about 50MB of memory, you can load your firefox profile into ram

this speeds up firefox quite a bit on my end

[http://forums.gentoo.org/viewtopic-t-717117.html](http://forums.gentoo.org/viewtopic-t-717117.html)

on this computer i have windows 7, and an assortment of linuxes, previously had vista on here, and last laptop had XP before i put linux on it

while i haven't used windows much for quite some time, Linux always seems faster when i do have to use it.  just in general application load times and such

---

### Post by xoorox on 2009-03-03
Up until the most recent iteration of Firefox I'd have said Ubuntu was noticeably faster than XP... with 8.10 and FF3 I've found java and javascript to always be the thing causing speed problems... it's now noticeably slower. I remain optimistic that the next iteration of FF will improve things... it's not so much slower that I get too wound up about it :)
 
p.s. thtrgremlin hit the nail on the head with the list of reasons Windows is annoying.  there is definitely a bit more tweaking involved to get Ubuntu set up right but for usability and performance it's a clear winner.  my only reason for keeping XP going is music software and my studio setup.

---

### Post by goldblattster on 2009-03-03
> **kelvin spratt said:**
> My cpu runs at about 20% running flash with firefox with compiz running with full bells and whisttles and downloading at the same time. I would suspect its your graphics card pulling down your processor. A lot of graphic cards really don't work well with linux I now use a Nvidia with 510mb of internal ram and those glxgears run at 4,900 fps without compiz and 3,900fps  my old Ati card ran at 1,400fps without and 600fps with, and stole a lot of cpu youtube was crap now runs in fulscreen with no problems.

I completely agree with that.

---

### Post by ambdeep on 2009-03-03
I believe the exact opposite to what is said in the first post........I have been using Windows for the past 11 years and it wasnt half as good as linux has been(ive been using it for abt 2 months)!!!!!!!!

---

### Post by Hadraniel on 2009-03-03
Please don't turn this topic into some religious linux vs. windows war.

I agree to the thread starter: Flash sucks big time in Linux, or, at least, Ubunutu. I currently don't use other distributions outside VMs, so I don't know how it's like e.g. with Fedora.

Flash Media inside of Firefox ist noticably slower than on Windows XP.
Flash Media inside of Opera (my favourite Browser) is, besides from being pretty unstable, choppy, crappy and basically useless.

First issue indicates general trouble with Adobe Flash Plugin (v10 is still alpha anyway, isn't it?), and second problem is some Opera issue for sure.

Unfortunately, I don't see any chance to improve this annoying situation, as Adobe has their hands tight on this proprietary virus called Flash, and Linux as Desktop OS generally still does not have the grade of recognition as it deserves.

---

### Post by xtremethegreat1 on 2009-03-03
Firefox with Flash Player is really the culprit. I don't have a graphics card, and suffer from the system's getting sluggish. :(

---

### Post by eldragon on 2009-03-03
> **xtremethegreat1 said:**
> Firefox with Flash Player is really the culprit. I don't have a graphics card, and suffer from the system's getting sluggish. :(

i must say, ive upgraded to xorg-server 1.6 and things got really much better....

i cant compare it to windows since i dont have where to do it :D

---

### Post by sandy8925 on 2009-03-28
Has anyone here tried gnash or swfdecoder ? And yes I agree Flash sucks bigtime on Linux and I think it's bcos they're more interested in developing or Windows and not bothered with performance of Flash in Linux.Although I must say using the latest Nvidia 180 drivers in 8.10 has sped things up considerably.

---

### Post by Firidan on 2009-03-28
I think that firefox and flash run much faster in ubuntu than in windows. On my vista laptop (AMD Turion MK-36 2 GHz, 1 Gb ram, Ati Xpress 1100) it takes firefox about 7 seconds to start - ubuntu 1 second. RAM usage in ubuntu is about 300 Mb with maximum visul effects when ubuntu is idle and about 400 Mb when I launch firefox.

My advice is: Buy a new computer! If you are happy with how XP runs on your computer (By the way how old is it? 8, 9 years?) I'm pretty sure that a PC with pentium dual core and 2 GB RAM will be more than enough for you.:lolflag:

---

### Post by donotaskwhoiam on 2009-03-29
In my experience, firefox with flash is a little slower than it is on XP.

And flash applications have a serious problem with ubuntu. I made a new thread about it for help, but get no reply since a week ago. If you would like to help me a bit, check it here please: [http://ubuntuforums.org/showthread.php?t=1109713](http://ubuntuforums.org/showthread.php?t=1109713)

Sorry for my English. Thank you.

---

### Post by AR_Kozz on 2009-03-29
Firefox was born to crash, and I doubt that Mozilla will ever fix that. It is just too cpu-hungry, and like all "popular" warez, they try to add as many bells and whistles as they can which guarantees that Firefox will always be like an SUV to your cpu's gasoline.

You can beat the flash problem with some specific bells and whistles. Flash in linux sucks, period. Whoever says its the graphic card must have lucked out and have one of the few cards where it works well. Adobe has never made a good flash player for linux.

But Mplayer has! You could try open-source flash alternatives like gnash, but Mplayer is much better. VLC can handle flash too. Getting Firefox to use them instead of flashplayer plugin is a hassle, but if you get the Greasemonkey add-on, there are plenty of user scripts for various sites that force Firefox to use mplayer for flash. They also allow you to download the video before viewing it. For firefox 3 there is a downloadhelper add-on that is supposed to allow you to download flash from just about anywhere, and convert it to more manageable format too. 

Those solutions don't make the video look good in real time though. That's cause nobody gave anybody money to make a linux flash player, and that's that.

---

