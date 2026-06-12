---
title: "Desktop Wallpapers - CompizFusion - Cube"
date: 2009-02-12
forum: General Help
---

### Post by estrong07 on 2009-02-12
Hey everyone! Complete noob to Ubuntu (v8.10) here, but have been doing rather well thanks to all of your helpful Forum Posts and Tutorials. This community rocks!!

Anyways, on to my problem, I really hope someone can help me out. I have already searched the forums for about two days now, and cannot seem to find a solution that works for me. 

[ My Issue ]
Unable to set a different wallpaper for each viewport, as I have seen in countless YouTube videos, and even posts on this forum. Attempting to assign a different wallpaper to each face of my 'Desktop Cube'.

[ My Actions ]
1.) Downloaded Ubuntu 8.10, installed onto my second HDD (was a breeze!)
2.) Added the CompizFusion repository, used plugins to enable the 'Cube Desktop' and the 'Wallpaper' plugin, among others
3.) Set (4) custom wallpapers in CompizFusion, one for each side of the cube
4.) Using 'gconf-editor' via Terminal (as root), went to 'Apps --> Nautilus --> Preferences', and unchecked 'Show Desktop'
5.) Logged out of Ubuntu, Logged back in; my custom wallpaper appeared very briefly, then went right back to the standard Ubuntu wallpaper. Restarted the machine, same results.
6.) Returned to 'gconf-editor', and verified that 'Show Desktop' was still unchecked under Nautilus Preferences.
7.) Using 'gconf-editor', also uncheked the option to show the GNOME desktop
8.) Verified that the custom wallpapers were still set in CompizFusion
9.) Logged out of Ubuntu, logged back in; custom wallpaper appeared briefly, then returned to the default Ubuntu wallpaper
10.) Restarted machine; custom wallpaper appeared briefly, then returned to the default Ubuntu wallpaper

[ Notes ]
The custom images I am using are '.jpg' images stored on HDD 1, while Ubuntu is installed on HDD 2. I wouldn't think this would make a difference though, as I can apply these same images as 'caps' in the 'Desktop Cube' plugin, and open and manipulate them fine in Ubuntu.

I am not really sure what I am missing here, since I am a complete Linux / Ubuntu / CompizFusion noob, it is probably something simple that I am just overlooking. This is the first time that a process posted in this forum has not worked for me in Ubuntu, would really like some help with this. 

If there is any additional information that I could post that would help anyone in providing me a soultion, I will happily provde it. Thanks in advance!!!!

[ UPDATE ] Finally got it working, by following this post TWICE (first time still didn't work for some reason): [http://ubuntuforums.org/showpost.php...4&postcount=39](http://ubuntuforums.org/showpost.php...4&postcount=39)

---

### Post by Ben Page on 2009-02-12
maybe this guys "how to" can help you

[http://my.opera.com/ubuntunerd1/blog/?startidx=0](http://my.opera.com/ubuntunerd1/blog/?startidx=0)

---

### Post by laceration on 2009-02-12
I have 6 wallpapers on my 6-sided "cube" and do not have the wallpaper plugin.  I believe the wallpaper plugin is to change your wallpapers automatically every 5 or whatever minutes.  _It is not where you set your wallpapers._  In ccsm, go to desktop cube, appearance tab and add your images to Background Images.  You shouldn't need to reboot or anything, it might take 15 seconds to change though.

---

### Post by estrong07 on 2009-02-12
> **Ben Page said:**
> maybe this guys "how to" can help you

[http://my.opera.com/ubuntunerd1/blog/?startidx=0](http://my.opera.com/ubuntunerd1/blog/?startidx=0)
Thanks for the reply, but this tutorial covers the exact same steps that I listed above. I have already performed all of them, to no avail.

---

### Post by estrong07 on 2009-02-12
> **laceration said:**
> I have 6 wallpapers on my 6-sided "cube" and do not have the wallpaper plugin.  I believe the wallpaper plugin is to change your wallpapers automatically every 5 or whatever minutes.  _It is not where you set your wallpapers._  In ccsm, go to desktop cube, appearance tab and add your images to Background Images.  You shouldn't need to reboot or anything, it might take 15 seconds to change though.
Thnaks for the reply, but I have defined (4) images in this location 'Desktop Cube', one for each of the (4) sides of my cube. The images have been set here with no results. Then the images have been set in the 'Wallpaper' plugin with no results. Then the images have been set in *both* locations, with no results.

---

### Post by laceration on 2009-02-12
hmmmm...that is perplexing, it seems like it should be working.  Maybe there is some kind of conflict w/ the wallpaper plugin, try deselecting it.

---

### Post by estrong07 on 2009-02-12
> **laceration said:**
> hmmmm...that is perplexing, it seems like it should be working.  Maybe there is some kind of conflict w/ the wallpaper plugin, try deselecting it.

I finally got it worked out by following the tutorial here: [http://ubuntuforums.org/showpost.php...4&postcount=39](http://ubuntuforums.org/showpost.php...4&postcount=39)

The images set in the Wallpapers plugin are the ones that appear, and work fine; images set in the 'Desktop Cube' plugin do not work--from what I can tell, those are for the 'Caps' (top and bottom) only.

Anyways, I followed the tutorial above, and the first time it still didn't work. Walked through it a second time, and it worked like a charm. 

Thank you for your suggestions.

Can you tell me how to set this post as 'solved', as I have seen on other posts in the forum?

---

### Post by hatten on 2009-02-14
It's not possible at the moment. They disabled it along with the "thank" buttons a while ago. It might be back someday.

---

### Post by xtracool_protik on 2009-11-15
Hi,
 Am I missing something? If I click on the link it takes me to ubuntuforums instead of any particular post
 By the way other thing -- I can't even tick wallpaper plugin if I tick it it gets automatically unticked immediately.
 However it seems it tried to do something 
 Ohh and I don't have session in my system --> preferences

---

### Post by timmyhiggy on 2010-03-19
I can't seem to get the multiple backgrounds working either. I have 4 desktop backgrounds in the CCSM wallpaper section, and nautilus' "show_desktop" disabled in gconf-editor, but I'm still stuck with the same background as I had before. I'm using Ubuntu Netbook Remix, although I wouldn't have thought this would introduce any problems.
And I guess the thread that is linked to a couple of times in here has been deleted...

---

### Post by thefallofroy on 2010-03-19
I can't even get my desktop cube thing to work...

---

### Post by myk02k on 2010-03-21
Same problem here since I upgraded to Karmic.

---

### Post by myk02k on 2010-03-21
I just fixed the problem.  This may help all of you who followed the previously cited HOWTO but still do not have multiple wallpapers.

In a terminal, type:

```
gconftool -t bool /apps/nautilus/preferences/show_desktop -s false
```

---

### Post by myk02k on 2010-03-26
I think I fixed this issue with the above fix, yet no one posts to confirm this???

---

### Post by gfunkera on 2010-03-26
> **estrong07 said:**
> I finally got it worked out by following the tutorial here: [http://ubuntuforums.org/showpost.php...4&postcount=39](http://ubuntuforums.org/showpost.php...4&postcount=39)

The images set in the Wallpapers plugin are the ones that appear, and work fine; images set in the 'Desktop Cube' plugin do not work--from what I can tell, those are for the 'Caps' (top and bottom) only.

Anyways, I followed the tutorial above, and the first time it still didn't work. Walked through it a second time, and it worked like a charm. 

Thank you for your suggestions.

Can you tell me how to set this post as 'solved', as I have seen on other posts in the forum?


for some reason that link isnt working properly for me... can you please repost?

---

### Post by ScottG89 on 2010-12-10
I am having a problem getting multiple desktops as well. I enabled "Wallpaper" in compiz and disabled show desktop in gconf-editor, but it looks to have just deleted the whole desktop in general. ie. I can see right through my cube and just see my skydome picture. If I un-check wallpaper then the first picture in the list of backgrounds shows up but none others.

---

### Post by rothbart on 2011-02-18
> **gfunkera said:**
> for some reason that link isnt working properly for me... can you please repost?

The guy copied/pasted the URL as quoted (it had ... in it), here is the correct URL he was referencing... I'm not sure if it'll help (I'm in the middle of trying to fix it on my system too but I figured I'd update this thread to have the correct URL)

[http://ubuntuforums.org/showpost.php?p=5691394&postcount=39](http://ubuntuforums.org/showpost.php?p=5691394&postcount=39)

Not the difference between the URL shown when you hover over that link and the text displayed above. ;)

---

