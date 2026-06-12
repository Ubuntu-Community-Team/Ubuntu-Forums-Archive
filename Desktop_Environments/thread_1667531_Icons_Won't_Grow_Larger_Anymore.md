---
title: "Icons Won't Grow Larger Anymore"
date: 2011-01-15
forum: Desktop Environments
---

### Post by Laysan_A on 2011-01-15
Hi,

I was trying to sort through a mass of files from a recovery (I was tired and formatted my wife's /home), with dolphin. I set it to preview and moved the slider all the way to the right so I could see without opening the files.

Well, as you probably know, kio_thumbs tends to get greedy when it has a lot to do, and somewhere along the way it crashed plasma, and afterward, though the previews seem to work normally, my icons (most of them anyway - exceptions seem to be the "T" icon for text files, and the green page with the recycle symbol for backed-up text files) no longer get any larger than about, oh, 32x32? They'll get really small, and I can use the slider to make them larger, until, say, 32x32, then they revert to an even smaller size and stay that way as the slider continues to move to the right. This appears to be system wide - both dolphin and folder view are affected. Oddly, in dolphin, when I slide the slider to the right the space for the icons gets larger, while the icons stay the same size.

I left out the best part...All my recovered files were owned by root. Rather than change permissions (I was still tired), I opened dolphin with sudo. I think I somehow changed the permissions for the icon view to root, although I have no idea how that could happen. 

I would really appreciate any help with this. I have already reinstalled, both kubuntu (lucid) and windows at least half-a-dozen times each in the past two weeks or so, and my wife is really jonesing for her computer. I'm getting really tired of reinstalling...

---

### Post by Laysan_A on 2011-01-16
BUMP

Anyone?


Edit:
I just opened a rooted dolphin (kdesudo this time) so I could copy my apt folder to my (wife's) home dir., and the icons were all nice and big (still small outside root).

---

### Post by Laysan_A on 2011-01-18
Someone here MUST know SOMETHING about how this works! Talk to me! I don't expect a perfect fix - just a little help.

---

### Post by Laysan_A on 2011-01-19
Another bump...

---

### Post by Laysan_A on 2011-01-21
No one?

---

### Post by Krytarik on 2011-01-21
I'm so sorry that you didn't get any replys until now! This seems to happen from time to time.

I have to say that I don't really know KDE, but from what you are describing it seems to be permissions related. Check the ownership of the files in that home directory, if they still are owned by root, change it like this:
```

sudo chown USER.USER -R /home/USER
```After that re-login.

Greetings.

---

### Post by Laysan_A on 2011-01-22
Hey! Thanks for the reply!

Yeah, I already did that (graphically, at least). I opened a rooted dolphin to my wife's /home/username folder and changed the permissions in the properties section to apply to all subfolders and their contents. Didn't help. But just to be on the safe side I did the terminal thing anyway - didn't change anything.

I think - well, I don't know what to think. Most of these kinds of configuration files are in the home dir., but I don't think this one is. I bet it's some obscure file for x, or qt, or plasma, hidden away in etc, var, or usr. 

I wonder...since root doesn't seem to be affected, it seems reasonable to assume that it's tied to her acct., or group. I've never messed with this before, so I have no idea how difficult it would be, but I wonder if it would be reasonable to create another acct. and move all her stuff to the new /home/username, then just delete the original acct. and group?

I know there are some issues re. the original installation acct., and admin. privileges, but they're not unresolvable, are they?

Nice avatar, btw.

---

### Post by Krytarik on 2011-01-22
> **Laysan_A said:**
> 
Nice avatar, btw.
Thanks, had some time to find the right, one-fits-it-all one.
You can grab one here:
[http://tux.crystalxp.net/en.html](http://tux.crystalxp.net/en.html)

To your issue ;-):

I'm pretty sure that the respective config file is somewhere in the home directory.
Try to google it with the right keywords.

You may a look into ~/.xsession-errors for error messages.
If you don't find any reasonable hints in there to fix the issue, you have two options:

You can try to strip down the home directory to the essential things, like app config dirs, of course not logged in as that user at that time. Or you can create a new user and move those there. Those commands should be sufficient to create the new user and grant it admin rights:
```
sudo useradd NEW_USER
sudo passwd NEW_USER
sudo adduser NEW_USER admin

```
of course you can also use the GUI via "System -> Administration -> Users and Groups".

---

### Post by Laysan_A on 2011-01-22
Thanks Krytarik. I spent an hour or so going through the tuxes on that site. A lot of really good work, and some fun stuff.

I checked her xsession-errors file and didn't see anything obvious, so I suppose I'll have to create a new user acct. for her. 

I've already spent a fair bit of time going through various config files, both in home and elsewhere, and didn't find anything. It would have to be fairly obvious for me to find it though. I don't really understand standard bash expressions. 

Well, thanks for your help. I won't be able to do this until she's off her computer (I can't commandeer it again so soon after she's gotten it back). If I need anything more I'll repost.

---

### Post by Krytarik on 2011-01-22
I've done a short web search on that matter:

Check and compare the permissions of the directory where the thumbnails are stored, should be: /home/USER/.thumbnails . And try purging anything in it.

---

### Post by Laysan_A on 2011-01-22
Thanks, I'll try it. It'll have to wait 'till tomorrow, though.

What did you search (if you remember)?

---

### Post by Krytarik on 2011-01-22
> **Laysan_A said:**
> Thanks, I'll try it. It'll have to wait 'till tomorrow, though.

What did you search (if you remember)?
Just searched for path of the thumbnails directory, since I haven't a KDE system here to check. It now turned out to be the same as in Gnome.

---

### Post by Laysan_A on 2011-01-23
It was worth a shot, but unfortunately didn't change anything, (besides, it's my icons, not my thumbnails :))

---

### Post by Krytarik on 2011-01-23
> **Laysan_A said:**
> It was worth a shot, but unfortunately didn't change anything, (besides, it's my icons, not my thumbnails :))
Oh, then I've missinterpreted your initial post in that aspect.

---

### Post by Laysan_A on 2011-01-23
Well, I feel like an idiot. I spent hours on this, going through config. files I didn't understand, posting pleas for help, and just worrying about it, and all I had to do is change the theme.:oops:

All fine now...
(thanks so much for your help, Krytarik)

---

### Post by Krytarik on 2011-01-23
> **Laysan_A said:**
> Well, I feel like an idiot. I spent hours on this, going through config. files I didn't understand, posting pleas for help, and just worrying about it, and all I had to do is change the theme.:oops:

All fine now...
(thanks so much for your help, Krytarik)
But since you seemed to have the default "Radiance" theme running, I only took that into consideration shortly!?

EDIT: Oh, that was another thread. I didn't think of it in your case, that would be the icon theme, right?

---

### Post by Laysan_A on 2011-01-23
Yep. I was using Tango. I purged it with synaptic, then reinstalled it. Unfortunately, whatever configuration file that was affected survived the purge, so Tango (and tangerine) is no longer an option on my wife's computer - too bad.

---

### Post by Krytarik on 2011-01-23
Since imo there is no configuration file or whatsoever than the theme dir itself, I've looked up the dependencies of both themes: Both themes depend to a different extent on the packages "gnome-icon-theme" and "hicolor-icon-theme". Try purging and re-installing those, if you want.

---

### Post by Laysan_A on 2011-01-24
The partial dependency on gnome-icon theme concerns me a little. Since I'm a kde user, there's some black magic that goes on between gtk stuff and qt. It certainly won't hurt to try purging and reinstalling those packages, but I'm uncertain of the extent of the role qt plays, mediating between the gtk appearance and kde's. Well, it won't hurt to try.

I'll have to do it tomorrow, when the computer's free.

---

### Post by Krytarik on 2011-01-24
It's only about icons, no GTK, no QT, really!

EDIT: And even if it were (which is definetely not the case here), they're only packages, they get updated from time to time, nothing else are we doing with a reinstall, at the end.

---

### Post by Laysan_A on 2011-01-24
Okay, I was able to purge all the tango icons again, and the gnome icons, but the hicolor proved problematic. Apt wanted to take practically everything else with it, so I had to make due with aptitude Reinstall. It didn't work (the reinstall worked; the purpose of the reinstall didn't) :)

So, at least she can see the icons that do work. :)

Thanks for all your help, Krytarik. I really appreciate it.

---

