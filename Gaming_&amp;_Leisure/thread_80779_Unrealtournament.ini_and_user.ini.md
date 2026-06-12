---
title: "Unrealtournament.ini and user.ini"
date: 2005-10-23
forum: Gaming &amp; Leisure
---

### Post by BLTicklemonster on 2005-10-23
Okay, this is just wierd. I have tried two different version of loki unrealtournament to get ut working on my machine right. Neither of them will get me to where I can reconnect to a server once a map ends and changes to the next map.

Knowing that in windows, when I remove ini files, it will regenerate them, I dragged my unrealtournament.ini and user.ini files to my desktop and started ut up, and it kept all my preferences, settings, binds, everything. Why is it doing this? Where are the ini files it's using, and why can't I find them? I dragged the ut folder out of it's normal place in order to break any automatic linking it may have going on yet it still does this.

I think there's a setting in one of my ini files that may be causing my problem, but I can't work on it until I find the actual ini files.

Where would they be? The only loki folders I see are in /usr/local/games/ and one is update, the other is uninstall. Search only comes up with the ini files on my desktop. 

I am at wits end. The only other thing I can figure that would be causing me to hang in etherdweebville when the server logs me off is my nic. I have an onboard that isn't being used (it's disabled in bios), and the one I'm using is a dlink. I guess I could try the onboard and see if the nic is the problem, but I just don't see that being it.

---

### Post by BLTicklemonster on 2005-10-23
Well heck. I fixed the reconnect problem by doing this:

sudo /etc/network/interfaces 
address ******** (change * with the values of your ip address)
netmask ******* (idem)
gateway ******** (idem)
broadcast ********** (idem)dns
network ******** (idem)network ip 

Thanks to this thread [http://ubuntuforums.org/showthread.php?t=78449&highlight=CONFIGURE+INTERNET+CONNECTION](http://ubuntuforums.org/showthread.php?t=78449&highlight=CONFIGURE+INTERNET+CONNECTION)

---

### Post by Zeroedout on 2005-10-23
the reason moving the .ini files didn't work is because it sores it in /home/user/.ut2004  and in linux it ends with .conf

---

### Post by BLTicklemonster on 2005-10-23
You don't understand, not only is this not qUTake2k4, but UTGOTY, but there's nothing in my /home/bill/ that is UT related, ini, conf, lmnop, or otherwise.

So I got that taken care of... so I thought I'd be swift and upgrade to breezy. Once done, I had no internet. Nothing undone redone, reconfigured or disfigured would bring it back. I'm now on my 4th install of breezy. Lessons learned dictate that I probably will get way further this time before I totally dweeb out and have to reinstall for the 5th 6th 7th and 8th but last time. (8th because if it gets that far, I'm giving up and going back to windblows)

---

### Post by ranf on 2005-10-23
They are under .loki in your home directory:
```

ranf@schlepp:~ $ locate User.ini
/home/ranf/.loki/ut/System/User.ini

```

---

### Post by BLTicklemonster on 2005-10-23
No, weren't there either. 

Using a different version this time, 

sh unreal.tournament_436-multilanguage.goty.run


and for the first time, it has let me install it from terminal without saying I had to be super user, and it's saying the ut directory is /home/bill/ut/ and the link is /home/ut. Perhaps for once this will work.

Thanks for trying to give me a hand.

Oh, I downloaded the loki installer, bot versions of ut installer, the one above, and 

ut-install-436-GOTY.run

But opted to use the first one because the second one is the one I've been using all along, figured something different might help. Also didn't install the loki yet.

---

### Post by Biased turkey on 2005-10-23
[QUOTE=BLTicklemonster]No, weren't there either. 

Using a different version this time, 

sh unreal.tournament_436-multilanguage.goty.run


and for the first time, it has let me install it from terminal without saying I had to be super user, and it's saying the ut directory is /home/bill/ut/ and the link is /home/ut. Perhaps for once this will work.

Thanks for trying to give me a hand.

Oh, I downloaded the loki installer, bot versions of ut installer, the one above, and 

ut-install-436-GOTY.run

But opted to use the first one because the second one is the one I've been using all along, figured something different might help. Also didn't install the loki yet.[/QUOTE]

OK, just installed Ut on my 2 rigs 10 minutes ago.
1st rig:( firewall-router ) ATI radeon 9600 ( sound problem, but graphics OK )
2nd rig  ( gaming rig ) Nvidia 6600 everything works nicely )

1) of course, be sure your 3D acceleration drivers are installed
2) I downloaded both /home/bourdouj/ut-install-436.run
 and /home/bourdouj/ut-install-436-GOTY.run
 the 1st one works, the 2nd one doesn't
[ftp://sunsite.dk/mirrors/lokigames/patches/ut/ut-install-436.run](ftp://sunsite.dk/mirrors/lokigames/patches/ut/ut-install-436.run)
that's the one to get.
3) insert your UT cdrom
4) sudo bash ut-install-436.run
5) export UT_DATA_PATH=/usr/local/games/ut/System
6) sudo ut

And voila
just a smal detail: everytime I want to run UT I have to type the 5) line command.
If someone could tell me how to add permanently the 5) line II would be glad.

I hope my post helps.
B.T.

---

### Post by BLTicklemonster on 2005-10-23
Absolute frustration over here at this time.

Finally got the problem corrected, so I thought I would be swift and upgrade hoary to breezy. Fried the internet, and seeing that reinstalling everything is faster than picking through the miasma and hoping you find a reason why.

Got ubuntu up, ran easyubuntu. Funny, no nvidia drivers. glxgears just sits there. ut worked, but ran at 2 fps.

So I ran that other thing that arnie made. 

Same problem, but the nvidia glx drivers were there. Nothing would get them working.

Reinstalling for the what, 6th time?

This is getting really old. Really old. Even with windows, you could get back to square one without a reinstall if you were just installing drivers.


*edit: nvidia drivers loaded this time, splash screen and all. now to get ut installed in home/bill, then set the network interface correctly, and see what crashes this time.

---

### Post by BLTicklemonster on 2005-10-23
heh heh heh, scared the linux gods, I did. They thought they were going to lose me, so they laid off this time. Did everything the same again, and now everything works fine. 

Now to get the dvd ripping down.

But that's another thread in another section of the forums...


thanks for your help all.

---

### Post by BLTicklemonster on 2005-11-10
Okay, found the .loki directory, it was in /home/bill/ and it was hidden. 

Installed 2k4 just to see how it did, and of course it plays way better than it ever did in windows. But it's still 2k4, and I have a hard time playing it, so it's there for reference material purposes for my project. Shame that the editor doesn't work in linux.

---

