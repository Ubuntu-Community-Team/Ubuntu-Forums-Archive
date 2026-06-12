---
title: "COMPIZ: Dasboard water effect when releasing windows"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Tobba25 on 2006-09-22
Hope this is the right place to post... 

Anyway, got my Compiz running, with Quinns repos and all that. But how do I get that apple dashboard water-wobble release effect on my windows? And watertrail on mousepointer?

And I remember some talk about a dock, where is it? 

:rolleyes:

---

### Post by DoorGunner on 2006-09-22
I can answer the one about docking..... I am still new to this too. Most things I have discovered are by trying them.

most settings can be made using the Compiz Settings Manager. In the case of docking it is located in the Wobbly Windows section. Make sure that it is checked on. If you hold shift and move a window close to your KDE bar or one of you gnome bars it will suddenly lock to it. I am unsure if this can be done automatically. 

I dont know what you mean by water-wobble effect. I do know that if you ensure that the water is selected you can press shift+F9 you get a neat rain effect on the screen. (just press shift+F9 again to shut it off) 

Another neat effect is if you press a key to long sometimes you hear a bell. With water on the top bar of the screen will give a shimmering water effect....Pretty cool warning.

Have a look at the keyboard settings too (hint hint). A lot of this is by trial and error. 

food for thought

---

### Post by Tobba25 on 2006-09-22
Yes, I know about the shift+f9-effect. But that is just random waterdrops, I want my windows to react with the water. When I release them.

---

### Post by Rashid584 on 2006-09-22
I don't even understand what you mean, but it sounds pretty awesome.

I thought the water effect WAS the raindrops...what do you mean??

And the dock is a plugin, I think you might have to download and install that one seperately...I installed them from the repos on the wiki (not quinn) and it worked

-Rashid

---

### Post by diggity on 2006-09-23
I think the water effect you are looking for is not part of compiz. It's xdestopwaves.
Here's a thread about it:
[http://www.ubuntuforums.org/showthread.php?t=112333&highlight=xdesktopwaves](http://www.ubuntuforums.org/showthread.php?t=112333&highlight=xdesktopwaves)

---

### Post by Rashid584 on 2006-09-23
Oh, I know the water effect you mean.

The keybiding is broken for most people.

You need to go to CSM, Water Effect and Keyboard and change the bind for "Initiate".

CTRL + SUPER didn't work for me. Change it to something else. I used SUPER + X and it works. Its quite cool :D

If super isn't working for you at all, try this command

```
xmodmap -e "clear Mod4" & xmodmap -e "add Mod4 = Super_L"
```

Hope that helps!

-Rashid

---

### Post by Tobba25 on 2006-09-25
Oh, thanks guys! 

Allthough I was hoping that this was some openGL feature... Is it part for compiz :confused:

---

### Post by Tobba25 on 2006-09-25
> **Rashid584 said:**
> Oh, I know the water effect you mean.

The keybiding is broken for most people.

You need to go to CSM, Water Effect and Keyboard and change the bind for "Initiate".

CTRL + SUPER didn't work for me. Change it to something else. I used SUPER + X and it works. Its quite cool :D

If super isn't working for you at all, try this command

```
xmodmap -e "clear Mod4" & xmodmap -e "add Mod4 = Super_L"
```

Hope that helps!

-Rashid
Rashid,

Thanks man! Care to post some screens? :-) My ubuntu is way broken these days, have to get about to reinstall the whole thing...

---

### Post by Rashid584 on 2006-09-25
> **Tobba25 said:**
> Rashid,

Thanks man! Care to post some screens? :-) My ubuntu is way broken these days, have to get about to reinstall the whole thing...

Your welcome :)

OK, I'll try. Although CTRL + PRINT doesn't seem to do much for me :S

-Rashid

---

