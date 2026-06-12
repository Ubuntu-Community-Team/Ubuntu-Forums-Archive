---
title: "lost all desktop icons"
date: 2008-06-04
forum: Desktop Environments
---

### Post by jojuman on 2008-06-04
hello,
not only did i lose all my icons but i"m unable to open documents or pictures or any other folder.
Prior to this problem I did a system update but I'm not sure exactly what was updated.
Thanks in advance,

Is there a way to restart Nautilus?
thanks.

---

### Post by Happy_Man on 2008-06-04
There is a way. Press alt-f2 and enter ```
killall nautilus
```. That should automatically restart it for you.

---

### Post by jojuman on 2008-06-05
I tried killall nautilus as suggested from a previous reply and got the following back:
no process killed

Any ideas?

Thanks.

---

### Post by chronographer on 2008-06-05
maybe nautilus is gone? try typing "alt F2" and then entering "nautilus" see if it runs, if anything changes, you can reinstall it with "sudo aptitude reinstall nautilus" also check your settings in gconf-editor - apps - nautilus.

---

### Post by jojuman on 2008-06-05
Well, this is rapidly deteriorating. I've compared nautilus settings with my other ubuntu machine and everything appears to be the same. I'll try re-installing it later on today and see what happens. Also, for some unknown reason, my computer is locking up constantly and have to reboot to get it to work again. It just seems to me that all my problems started after I did the last system update. 

While this is frustrating it's also challenging and I guess it's a good way to get to know Linux a little more intimately.

Thanks.

---

### Post by jojuman on 2008-06-05
Would Compiz have a setting that hides all desktop icons as well as folders?

Thanks.

---

### Post by Happy_Man on 2008-06-05
> **jojuman said:**
> Would Compiz have a setting that hides all desktop icons as well as folders?

Thanks.
Yes, if you set Compiz to draw your desktop instead of Nautilus, you lose all your icons.

---

### Post by jojuman on 2008-06-05
Whoa, how do I return to having nautilus take care of the desktop? or better yet, if compiz is acting goofy, how do I disable it?

Also, al my keyboard shortcuts don't work anymore.
This is truly strange.

Any ideas?

Thanks.

By the way, I created another account and everything works fine. (for whatever this is worth).

---

### Post by jojuman on 2008-06-10
No luck so far. I hate to give up though so I'll keep messing with it on my spare time. 
Thanks for all the replies!

---

### Post by RealMabu on 2008-06-24
*Cross post from [http://ubuntuforums.org/showthread.php?t=814079]("http://ubuntuforums.org/showthread.php?t=814079")*
> 
Same for me too.
That was after an update that required a reboot.
I believe (but am not sure) that it was right after the release of 2.6.24-19-generic kernel.
So, symptoms:
-/home/myname/Desktop folder still exists and is in good health
-menu bar is fine too
-nautilus displays only the background and nothing can be done there (no new folder, no drag&drop)
-rebooting won't work for me
-under gconf-editor->apps->nautilus->preferences the "show desktop" checkbox IS checked. Tried to run gconf-editor as root also, same result: checked.

Oh, BTW, the OS is working fine, all apps run seamlessly and everything seems to be ok... just NO DESKTOP.

Any help?


---

### Post by antiOST on 2008-06-27
Hi 

Experienced the exact same problem while messing around with compiz, i'm been tweaking around since (thats how I saw this post). I got my menus and icons and almost all other lost functionality back, here's what I did.

Bear in mind, I'm a totally newbie (I married ubuntu 2 weeks ago :)) so there might be some unforseen consequenses I yet have to experience, so feel free to enlighten me.

1) I uninstalled everything realted to compiz through synaptic (search for compiz). After restarting X (ctrl+alt+backspace) my menu and icons etc where back.
At this stage I couldn't change workspace and other misc. stuff, which led me to the next step...

2) Enabling metacity ("metacity --replace" in a terminal) made my workspace work again, but my shortcuts didn't work and I didn't have any windows decorations. Guess compiz was still spooking around.

3) Then I setted the visual effects to none (System-> Preference->Appearance->visual effects), which gave my windows decoration back + shortcuts

I'm now running a basic desktop with everything working, no eye candy though, but I'll try to reinstall compiz when I get the time and see how  it goes. I was so close to reinstall the whole thing, so I have nothing to lose.

EDIT: I used this guide ([http://ubuntuforums.org/showthread.php?t=533201&page=2](http://ubuntuforums.org/showthread.php?t=533201&page=2)) to completely remove any compiz dependencies and installed compiz again (sudo apt-get instal compiz compizconfig-settings-manager) and now it works as expected !

Hope this helps
Kim

---

### Post by RealMabu on 2008-06-30
I don't use compiz.
BTW I found a workaround (I won't call it a solution since the problem periodically reappears...):
1) ctrl+alt+f1 then text-mode login
2) sudo /etc/init.d/gdm restart
3) ctrl+alt+f7 (if graphics login doesn't show itself...)

Hope this helps.

---

### Post by pablopanama27 on 2011-01-10
maybe nautilus is gone? try typing "alt F2" and then entering "nautilus" see if it runs, if anything changes, you can reinstall it with "sudo aptitude reinstall nautilus" also check your settings in gconf-editor - apps - nautilus.

This worked for me. Happened after i unistalled old versions of Vuze and thunderbird , since I was using the tar.bz new versions...

---

