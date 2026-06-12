---
title: "Xgl: No window borders/decorations"
date: 2006-09-14
forum: Desktop Environments
---

### Post by briansrapier on 2006-09-14
Hi. I now have Xgl up and running on my laptop (ATI Radeon Mobility M10 9700). Everything (so far) seems to work great with the exception of window borders and decorations. I am using a startup script as I did not want to modify my default session just in case it crapped out. The script is as follows:

STARTXGL.SH
-----------
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 2 && DISPLAY=:1
exec gnome-session
---

And then a startup script in my session preferences (default compiz-start):

COMPIZ-START
------------
#!/bin/sh
if ps -e | grep Xgl > /dev/null
then
    nohup compiz --replace dbus csm > /dev/null &
else
    nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null &
fi

sleep 2

if [ -f /usr/bin/cgwd ]
then
    nohup cgwd --replace &
else
    nohup gnome-window-decorator --replace &
fi
----

Like I said, it works great (posting this from it now), but decorations are missing. I went into gcompizthemer to try and see if tweaking would fix it, but nothing. 

Any ideas?

---

### Post by turbojugend_gr on 2006-09-14
Replace : 

```
#!/bin/sh
if ps -e | grep Xgl > /dev/null
then
nohup compiz --replace dbus csm > /dev/null &
else
nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null &
fi

sleep 2

if [ -f /usr/bin/cgwd ]
then
nohup cgwd --replace &
else
nohup gnome-window-decorator --replace &
fi
```

with:```
#!/bin/sh
if [ -f /usr/bin/cgwd ]
then
nohup cgwd --replace &
else
nohup gnome-window-decorator --replace &
fi

if ps -e | grep Xgl > /dev/null
then
nohup compiz --replace dbus csm > /dev/null & exit;
else
nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null & exit;
fi
```

Make sure you keep a backup of the old script first, then replace as above and save the file... Rebbot and start compiz! I believe your borders should appear, if not (kinda strange if so) then you can switch to your old script again till somebody else comes up with a better suggestion... MAKE SURE to provide i9nfo on how it went. Cheers

---

### Post by briansrapier on 2006-09-14
Nope.

BTW... Did I mention this is amd64? Does that make any difference?

Also, I noticed that on logout the options for shutdown and reboot are missing. (log out, lock screen, switch user, & hibernate are present).

---

### Post by turbojugend_gr on 2006-09-14
It seems to me you are behind the updates, try updating and then you will be ok. If not try changing to that script again, and if again you are unlucky try a search on this forums with the same topic. When I had this issue I found much help in [http://www.ubuntuforums.org/showthread.php?t=250489](http://www.ubuntuforums.org/showthread.php?t=250489) and in [http://www.ubuntuforums.org/showthread.php?t=252796](http://www.ubuntuforums.org/showthread.php?t=252796). I hope thay are handy to you 2.

---

### Post by briansrapier on 2006-09-14
Updates are not an issue. I have been constantly doing 'apt-get update' and 'apt-get dist-upgrade' since I started down this path a few days ago. Here are the repositories I am currently using:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main main-amd64 restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main main-amd64 restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main main-amd64 restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main main-amd64 restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main main-amd64 restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main main-amd64 restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main main-amd64 restricteddeb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main main-amd64 restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main main-amd64
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main main-amd64
deb [http://ubuntu.systemadministrator.org/](http://ubuntu.systemadministrator.org/) dapper eyecandy
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main main-amd64
deb [http://blog.space-based.de/2006/05/initngs-apt-repo-has-a-new-home/](http://blog.space-based.de/2006/05/initngs-apt-repo-has-a-new-home/) experimental main
deb-src [http://blog.space-based.de/2006/05/initngs-apt-repo-has-a-new-home/](http://blog.space-based.de/2006/05/initngs-apt-repo-has-a-new-home/) experimental main

Bloated, I know, but a few have been useful in my quest. Namely systemadministrator.org and beerorkid.com...

---

### Post by turbojugend_gr on 2006-09-14
Anyhow try checking these threads I tell you to, it would be a waste of time to continue contributing all the knowledge I earned in these discussions here, so if you don't find a good hint there, I can't help you either, It's not I don't want to, but I prefer you to look them up so you gain knowledge through them, you will need it. Let alone the fact I am sure your solution is absolutely there. ;)

---

### Post by gabrieliscool on 2006-09-14
i also have this problem. it seems that the update broke xgl.

my specs are as follows
intel pentium 3 ~ 1GHz
Nvidia GeForce 4 MX 440 PCI
384 MB of Ram
Latest Kernel From The Repo

---

### Post by briansrapier on 2006-09-21
OK. I did a LOT more research, tried other methods - including hacking gdm - but got no futher with the window borders. I did notice a few of the following items:

1) gconf - apps/compiz/general/allscreens/options only lists one key: audible_bell, nothing else.
2) gconf - apps/compiz/plugins has only one sub-heading: fade, nothig else.
3) csm - window decoration only has one option: transparency/brightness/saturation.
4) .cgwd.log is reporting that it is unable to open the following pixmaps:
menu
shade
unshade
above
unabove
sticky
unsticky

I know I'm missing something, but I don't know what.

---

### Post by briansrapier on 2006-09-26
Despite my frustration, I am continuing to work on why borders/titlebars are missing. I've been googling the H377 out of this issue and have tried just about everything I could find on the subject. 

I did run updates again on Monday and noticed that some of the scripts changed (compiz-start, etc). It seems that every other aspect of Xgl/compiz works, except window decorations and titlebars.

At least I have a much better understanding of how it works. 

So here is where I am at the moment:

sources.list:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main-amd64
deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main-amd64
deb [http://ubuntu.systemadministrator.org/](http://ubuntu.systemadministrator.org/) dapper eyecandy
deb-src [http://ubuntu.systemadministrator.org/](http://ubuntu.systemadministrator.org/) dapper eyecandy

gdm.conf:
1=Standard
GdmXserverTimeout=50

gdm.conf-custom:
[servers]
1=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -br -ac -accel glx:pbuffer -accel xv:pbufferflexible=true

compiz-start:
if ps -e | grep Xgl > /dev/null
then
    nohup compiz --replace dbus csm >> ~/.compiz.log 2>&1 &
else
    nohup compiz --strict-binding --indirect-rendering --replace dbus csm >> ~/.compiz.log 2>&1 &
fi
sleep 2
if [ -f /usr/bin/cgwd ]
then
    nohup cgwd --replace >> ~/.cgwd.log 2>&1 &
else
    nohup gnome-window-decorator --replace >> ~/.cgwd.log 2>&1 &
fi

When I go into gcomizthemer I noticed that, on the engines tab, all the engines but legacy have a red x. When I select a theme and quit, this appears in the .xsession-errors log:

"Usage: -i /file/to/install"

When I tried to install a theme manually, I got this:

"Invalid theme file. Does not end in .cgwdtheme."

I have tried removing and reinstalling cgwd, cgwd-themes, and cgwd-themes-extra, but no change.

Another couple of quirky things that I noticed are sound does not work when I start Xgl and, when I log out, I have to wait a minute or two before logging back in or the X server crashes.

Assistance with any (or all) of these items would be greatly appreciated.

Thanks.

---

### Post by turbojugend_gr on 2006-09-26
OK in my first post (post #2) IO suggested to use a specific script, in your last post you use sth else, which I can't see it doing a good job with gnome-window -decorator, which can explain you are still lacking boarders.

SO try to change your compiz starting script as I suggest in post #2 and you are likely to get decorations.

If you fail once again to solve this issue, I suggest you should follow [this]("https://help.ubuntu.com/community/CompositeManager/Xgl") how-to, re-doing the whole thing hopefully right. OH remember to remove the repositories you added in your previous install of xgl-compiz so you don't have messed repos.

Let me know how you progressed on that. ;)

---

### Post by briansrapier on 2006-09-27
No dice. Yes, I modified the startup script (multiple times) but it affected nothing. If that were the cause of the error, I would expect that it more than just decorations would be screwed up.

But, I went ahead and started fresh from the ground up. I followed the Howto in your last post. The only issues I met with were that it said to install csm which now appears to be part of compiz-gnome installation. I also went back to using the fglrx drivers, which never really worked as well as the ati or radeon driver (in my opinion). When I did, I noticed that the display is very grainy and performance gets choppy when opening/closing windows. But, still not decorations.

So, I'm no better off than I was on day one. I have tried every howto I could find, even non-ubuntu ones, without a bit of chance of getting decorations to work. The only clue I have is that I see the following error in my logs everytime I try to select a theme:

Usage: -i /file/to/install

I thought that it might have been related to the fact that there are no files in the themes directory that contain a .cgwdtheme extension. I downloaded a few new ones from gnome-look.org just to test. But, I quickly figured out that wasn't the issue. Even though I installed a .cgwdtheme extension, it loads into the same format as the others. (It's hard to explain it unless you've done it.) Long story short, I'm still hosed up as far as titlebars and window decorations go. 

Trust me when I say that I am not sitting here waiting for someone to hand me the answer. I have been digging to find the answer on my own, but I'm pretty much dug out. I've read so many howto's and forums and blogs related to compiz/xgl that I'm surprised that I know which way is up.

Thanks for the help, but maybe it's time for me to go back to doing things from the command line and forgetting about this for a while...

---

### Post by turbojugend_gr on 2006-09-27
I am really sorry I can't help you on that, it seems it is something really rare going wrong. It could be the drivers, the card I don't know... nore am I able to find out, since you sound too disheartened (I can't blame you, you are so unlucky) to go on. Anyhow I am sorry I was no good on that...

---

### Post by briansrapier on 2006-09-28
Frustrated, but not disheartened. I honestly don't feel that it is an issue with the drivers or the card because everything else works. 

I think I'm going to go back to the settings that gave me the best results, then go from there. 

I plan on continuing to post my findings in this thread to first provide a source of knowledge to those having similar issues and in hopes that something may trigger a response from someone else. 

I appreciate all the input and assistance.

---

### Post by JohntB on 2006-10-22
I'm having the same problem as you, and I'm using amd64 as well. Might there be a problem with the packages for that? Have you managed to fix the problem?

---

