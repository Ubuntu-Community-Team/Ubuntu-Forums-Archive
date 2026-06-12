---
title: "How To: AWN OS X &quot;Mod&quot;"
date: 2007-07-29
forum: Desktop Environments
---

### Post by Niklas Schröder on 2007-07-29
**This thread is now obsolete.**
*Please refer to this thread, [http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard+avant](http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard+avant) , to learn how to install and configure the new version of AWN which includes this feature.*

> 
Ok, there are almost always misunderstandings when people modify their OS to look some other OS. This is NOT about "I want a mac" or "I want OSX". If I would want a mac, I would go and buy one of those. No, this is simply about having fun by imitating and finding the limits of Gnome desktop. I often read that Gnome is considered very plain and not very configurable. I can't agree with that. Gnome is usable and simple, but yet very powerfull and it is possible to modify Gnome into anything you want. Now, I challenge KDE and OSX users to do the same. Can you make your KDE to look OSX as well as Gnome can imitate it? Or can you change your OSX to look Gnome, KDE or Windows? I doubt it, but I love to be proved wrong! ;)

Just to be clear, I don't want that OSX-look would be the default look of the Gnome. Gnome is beautiful with Tango icons and it should continue to follow it's own clean and usable style. I'm glad I made that clear. :) Now, let's begin...


[IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/awn.png[/IMG]

**I'm including complete, step-by-step instructions, and a version for more advanced users.**

*Complete:*

1. Click "System>>Administration>>Synaptic Package Manager"
2. Type in your password if prompted
3. Click "Search" in the top-center part of your screen
4. Type "avant-window-navigator" and hit "Enter"
5. Left-click on the empty box next to "avant-window-navigator"
6. Click "Mark for installation" in the menu
7. Agree to install the other files it mentions
8. Allow it to install
9. When it's finished, close Synaptic Package Manager
10. Hit "Alt>>F2"
11. In the new window, type "gconf-editor"
12. Navigate to "Apps>>Avant Window Navigator>>Bar"
13. Change "bar_angle" to "45"
14. Change "icon_offset" to "15"
15. Close gconf-editor
16. Hit "Alt>>F2"
17. Type "avant-window-navigator"
18. Hit enter

*Advanced User:*

1. Open "Synaptic Package Manager"
2. Install "avant-window-navigator"
3. Open "gconf-editor"
4. Navigate to "Apps>>Avant Window Navigator>>Bar"
5. Change "bar_angle" to "45"
6. Change "icon_offset" to "15"
7. Type "avant-window-navigator"

*Also posted on my blog:* [http://paperclipsandscrambledeggs.blogspot.com/2007/07/101st-post.html](http://paperclipsandscrambledeggs.blogspot.com/2007/07/101st-post.html)

---

### Post by rainbowed_man on 2007-07-30
Hi.

I suggest that you shorten the installation instructions for AWN to "Install the avant-window-navigator package if you haven't already. See https://help.ubuntu.com/community/InstallingSoftware.", because this is meant to be a How To modify AWN to act like OSX.

- Kyle Brooks, aka "rainbowed_man" on the Ubuntu Forums

---

### Post by Psyphre on 2007-08-01
Hey, i tried following your instructions but there arent any options to change the angle or icon offset in avant-window-navigator > bar in gconf editor.
Im confused :confused:

---

### Post by Niklas Schröder on 2007-08-01
have you had AWN installed for a while?  like for a month or two?

---

### Post by Nekiruhs on 2007-08-01
> **Psyphre said:**
> Hey, i tried following your instructions but there arent any options to change the angle or icon offset in avant-window-navigator > bar in gconf editor.
Im confused :confused:
There aren't any. Right now you have to compile AWN yourself with a patch to achieve this effect.

---

### Post by Motoxrdude on 2007-08-01
Sweet, worked for me.

---

### Post by Niklas Schröder on 2007-08-01
i didn't compile it and i have the effects right out of Synaptic...

---

### Post by walkerk on 2007-08-01
> **Psyphre said:**
> Hey, i tried following your instructions but there arent any options to change the angle or icon offset in avant-window-navigator > bar in gconf editor.
Im confused :confused:

surely you need a newer version.. give [reacocards thread]("http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard+avant") a look

---

### Post by Niklas Schröder on 2007-08-01
yeah.  that's what i was trying to get at.  if you're missing any variables mentioned in this tutorial, you need to get a newer version...  i could tell you one way of doing it (the way i would use), but my way would get rid of all custom settings...  so...

---

### Post by Sunflower1970 on 2007-08-01
> **Psyphre said:**
> Hey, i tried following your instructions but there arent any options to change the angle or icon offset in avant-window-navigator > bar in gconf editor.
Im confused :confused:

If you're on Edgy, you won't have these effects. It's only Feisty and above.

---

### Post by Niklas Schröder on 2007-08-01
you sure about that?

---

### Post by Sunflower1970 on 2007-08-01
A few weeks ago, when I had Edgy on my laptop. I was looking to do the OSX dock on it, and couldn't get it to work. I came upon a post or a blog somewhere that said it wasn't going to be ported for Edgy. That could have changed by now, but at the time it wasn't possible to do. (this was about 3.5 weeks ago)...This, amusingly, is one of the many, many reasons I went ahead and upgraded to Feisty on the laptop.

---

### Post by FuturePilot on 2007-08-01
```
deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator

```
These are the repos I used. It has the latest AWN.

---

### Post by Psyphre on 2007-08-04
I tried upgrading to feisty and then used the repos provided by futurepilot to install AWN. Yet I still dont have angle or offset :confused:

---

### Post by Niklas Schröder on 2007-08-05
here's what should be a way to fix it.

1. If you have any custom icons set, navigate to "/home/USERNAME/.awn"
2. Copy the "custom-icons" directory and place it somewhere safe
3. Open "Synaptic Package Manager"
4. Browse to "avant-window-navigator"
5. Completely un-install it
6. Click on "Mark All Upgrades"
7. Apply
8. Browse to "avant-window-navigator"
9. Mark for installation
10. Install
11. Open "gconf-editor"
12. Navigate to "Apps>>Avant Window Navigator>>Bar"
13. Change "bar_angle" to "45"
14. Change "icon_offset" to "15"
15. Type "avant-window-navigator"

---

### Post by Psyphre on 2007-08-05
WOW works perfectly now!!! Thank you very much :) . Appreciate your help!

---

### Post by Niklas Schröder on 2007-08-05
DUDE!  my suggestion actually worked!  THAT'S a first.  :p  and you're welcome.  :D

---

### Post by averageidiot on 2007-08-06
I have that same problem that those options arent available. I've tried removing it and reinstalling it and its the same. Which one do i choose from synaptic, avant bzr or avant svn?? And for some reason even when i have completely removed it, it still shows up in gconfg editor. Is there a way to remove it from there so maybe the new settings can be added once i install it again?


thanks!

---

### Post by NoSmokingBandit on 2007-08-06
the svn version is the most updated, so go with that. To uninstall it better, in synaptic choose to uninstall the packages completely, erasing all settings and stuff like that.

---

### Post by Sunflower1970 on 2007-08-06
AWN has moved from svn to bzr..so the bzr one is the most up to date. It has the option for stacks, and the 3D bar, plus there is now an option in the Preferences to change the bar from the flat look to 3D. No more using gconf for it :)

---

### Post by Niklas Schröder on 2007-08-06
hmmm...  i don't see the bzr one...

---

### Post by NoSmokingBandit on 2007-08-06
> **Sunflower1970 said:**
> AWN has moved from svn to bzr..so the bzr one is the most up to date. It has the option for stacks, and the 3D bar, plus there is now an option in the Preferences to change the bar from the flat look to 3D. No more using gconf for it :)

Oh crap, i was just on their forum a few days ago where someone said the svn was the newest. Screw that, im going with what you say.

---

### Post by Sunflower1970 on 2007-08-06
[quote=Niklas Schröder]hmmm... i don't see the bzr one...[/quote]

You have the repos, right? 

```

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator

```
 ([http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard+avant](http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard+avant)) for the gpg keys and such

That's all I have, and in Synaptic I have three different AWN versions. a much older version of AWN (I think it's the Ubuntu repos version) then a SVN version and a BZR version. 

I understand the SVN version will not be updated any more and for new features to use the BZR version.

---

### Post by ayoli on 2007-08-06
my two cents here: you need to 
```
sudo apt-get remove avant-window-navigator-svn libawn-svn 
```
before tryin to install the bzr one

---

### Post by FuturePilot on 2007-08-06
Wow! These stacks are cool!:guitar:

---

### Post by walkerk on 2007-08-06
> **FuturePilot said:**
> Wow! These stacks are cool!:guitar:

Are they? I have them and honestly.. bleh. What's the point? Just my opinion.

---

### Post by NoSmokingBandit on 2007-08-06
i installed the new version and i dont have stacks. Is it a patch?

---

### Post by jackmc on 2007-08-06
> **NoSmokingBandit said:**
> i installed the new version and i dont have stacks. Is it a patch?

wondering the same thing...

---

### Post by FuturePilot on 2007-08-06
Did you right click>Configure Applets>Add>Stacks?

---

### Post by jackmc on 2007-08-06
I tried, but it is not there - I'm still pretty new here, I'm waiting for it to be released (I dont know how to patch it) - NoSmokingBandit was asking whether you need to still patch awn, or if stacks are included already..

---

### Post by FuturePilot on 2007-08-06
If you have the bzr version installed it has stacks included. No need to patch. You must completely remove the svn version before installing the bzr version.

---

### Post by Niklas Schröder on 2007-08-06
i'd just like to point out that this isn't really a thread for getting help with AWN.  it was meant to be a short how to.  you're welcome to ask questions, but you may not get answers.  try here if you really need something.

[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum)

---

### Post by jackmc on 2007-08-06
> **FuturePilot said:**
> If you have the bzr version installed it has stacks included. No need to patch. You must completely remove the svn version before installing the bzr version.

Thanks, I found that I still had a bit of an old version left, must have conflicted. Stacking away now though :)

---

### Post by Sweet Spot on 2007-08-06
Anyone care to post a screen shot of this 'stacking' effect which is being talked about ? Would love to see.

---

### Post by ayoli on 2007-08-07
> **Sweet Spot said:**
> Anyone care to post a screen shot of this 'stacking' effect which is being talked about ? Would love to see.

see this [post]("http://ubuntuforums.org/showpost.php?p=3118816&postcount=21")

---

### Post by weblordpepe on 2007-08-07
yay!!

---

### Post by Niklas Schröder on 2007-08-07
**This thread is now obsolete.**
*Please refer to this thread, [http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard+avant](http://ubuntuforums.org/showthread.php?t=385981&highlight=reacocard+avant) , to learn how to install and configure the new version of AWN which includes this feature.*

---

