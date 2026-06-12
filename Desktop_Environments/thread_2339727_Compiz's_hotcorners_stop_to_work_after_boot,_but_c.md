---
title: "Compiz's hotcorners stop to work after boot, but comeback after I kill its process"
date: 2016-10-12
forum: Desktop Environments
---

### Post by cvgaviao on 2016-10-12
Hello,

I'm facing a strange issue with Compiz since I moved to 16.04.

When I restart my machine the hotcorners feature just stop to work. I can't see any log related to it. When I move the mouse cursor for any corner nothing happens.

But if I kill (using the system monitor) the compiz process, it will automatically be restarted and everything will comeback to normal again ! :/

could someone explain me why ?  is compiz using two different config files ?

thanks

---

### Post by mc4man on 2016-10-12
There aren't 2 'configs', there are your settings & the defaults. For anything set to a hot corner(s) the default would be disabled/not set.
So I guess when you boot up/login your settings or some of aren't being applied for some reason. 
What happens if you boot up, log in, log out & back in. Do the hot corners work?

---

### Post by monkeybrain20122 on 2016-10-14
I have been having this problem for the longest time (and mc4man has been very helpful in giving me advises) I think this may have something to do with hardware because in some machines I have the problem with almost every Ubuntu version while in others no so much. 

One way to fix this would be in ccsm go to Preferences > Plugin list , then disable auto plugins sorting and put "scale" towards the bottom of the list but above unity shell (if you put it below your desktop will crash) This is ok if you have just scale that needed to be put in the end, but  I also had wall and edge flipping it also needed to be placed at the bottom back in 15.04.
So here is another way and it worked 100% for me. 

Create a script called, say, fixhotcorner
```
#!/bin/bash
#fix scale hot corner
sleep 6
dconf write /org/compiz/profiles/unity/plugins/scale/initiate-all-edge '"Disabled"'
sleep 1
dconf write /org/compiz/profiles/unity/plugins/scale/initiate-all-edge '"TopLeft"'
exit 0


```

 Put script in your /home/username/bin (create the folder bin if it doesn't exist) make it executable by either right clicking > properties > allow to execute as a program 
or starting the terminal type
```
 cd bin
chmod +x fixhotcorner

```

Now make this autorun at login: in the dash, search for startup applications and add this to autostart applications.

Basically this resets compiz config for the hot corner automatically at start up. You may have to adjust sleep 6 in the first line depending on how long your login time is (time between typing in password and desktop loading) the number is waiting time before executing the next command (disable hotcorner) in sec, it has to be long enough for the desktop to load. So for example if your login time is 10 sec, then do sleep 12 instead of sleep 6. You may also have to edit which hot corner if yours is not top left


P.S. I so far don't have to do anything for 16.04. Maybe it is fixed, or maybe I just have a different computer.

---

### Post by monkeybrain20122 on 2016-10-17
Hmm The trick no longer works in 16.10. The gconf/dconf settings are still in  the dconf editor but changing them doesn't do anything, so apparently compiz is not controlled by dconf any more.

Change the script to

```
#!/bin/bash
#fix scale hot corner
sleep 6
setsid unity
exit 0
```

It would "work" but kind of drastic. You definitely would notice that the desktop is loaded twice after login. The best I can do is to make the sleep time shorter to so that it is less noticeable. In this case it seems that you don't need to wait for the desktop to load to issue the command like before

---

### Post by mc4man on 2016-10-18
> **monkeybrain20122 said:**
> Hmm The trick no longer works in 16.10. The gconf/dconf settings are still in  the dconf editor but changing them doesn't do anything, so apparently compiz is not controlled by dconf any more.


The commands should still work, tested here & the hot corner was set or disabled. (and was reflected in actual use.

---

### Post by monkeybrain20122 on 2016-10-20
> **mc4man said:**
> The commands should still work, tested here & the hot corner was set or disabled. (and was reflected in actual use.

It is strange. I have tested by actually disabling and enabling the hot corner in  dconf (instead of the script) and it still has no effect. On my system they all show up in dconf-editor as "no scheme found" . This is a 100% fresh (no old /home with left over config) minimalist vanilla install just for test, with no tweaking

The forgetting of hot corners and edgse seems to be hardware related. On a HP netbook not just scale, expose hot corner and wall edge flip also never work on reboot (but they worked in 16.04) and sorting plugins like before won't help. I cloned the system and restored it to an external hd and then boot off two other machines and for one everything works except for occasional glitches. On the other one scale hot corners and wall edge flip always work but expo failed 9 out of 10 times. .

---

### Post by cvgaviao on 2016-11-06
> **mc4man said:**
> 
What happens if you boot up, log in, log out & back in. Do the hot corners work?

Sorry, seem that I didn't receive a notification for this thread...

About your question, nothing happens... It just comeback to "normal" if I kill the compiz process...

---

### Post by cvgaviao on 2017-01-14
Last night I decided to try create another user account. it surprise me that there was no issue while using it.
So, using this new user account I've renamed the problematic older  account home folder, then created another one using the same name. After  that I just copy the important folders into the new account.
all issues gone and I kept all my user related data (bookmarks, keys, ongoing torrent downloads, etc) !!!

---

