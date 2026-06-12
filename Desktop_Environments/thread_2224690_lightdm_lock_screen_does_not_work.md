---
title: "lightdm lock screen does not work"
date: 2014-05-17
forum: Desktop Environments
---

### Post by srope01 on 2014-05-17
I have installed Lubuntu 14.04 on an IBM S50 ThinkCentre. When I try to manually lock the screen, for example by going to the shutdown panel button and selecting "Lock Screen", it doesn't do anything. Interestingly, if I go to the terminal and type out the command

```
dm-tool lock
```

then the lock screen sort of works. The whole screen goes blank with no password login prompt. If I hit return, then I get the login prompt so I can log back in.

Does anyone have any ideas of what is going wrong?

---

### Post by bapoumba on 2014-05-18
You are not alone, same here. <ctrl><alt><l>, **lxlock** or Logout Menu > Lock Screen do not work either for me. 
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1286686](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1286686)

```
bapoumba@SonyBlue:~$ light-locker-command
** Message: light-locker is not running
bapoumba@SonyBlue:~$ light-locker &
[1] 5415
bapoumba@SonyBlue:~$ light-locker-command -l
bapoumba@SonyBlue:~$ lxlock

```
Both last 2 commands work after starting light-locker. This is how far I've got when I looked at after a fresh install, as I like to lock my screen when I walk away..
Got the idea to test this from /usr/bin/lxlock

I'm not sure I'm on the right tracks because this does nothing :
```
bapoumba@SonyBlue:~$ lxsession-default lock
lock

Launching lock manager
```

Edit : I should add that leaving the computer unattended does blank out the screen and login is required after waking it up after running light-locker.

---

### Post by srope01 on 2014-05-18
Ah ok. So your solution would be a work around. If I start the light-locker process in a rc startup file somewhere, then the Lock Screen button would work. That would be good enough for me until they fix the bug. I will check that out and post it here when I figured it out.

---

### Post by bapoumba on 2014-05-18
I've added it to the Prefs > Default Apps for LXsession > Autostart tab. Not rebooted yet, will see if it works tomorrow.

---

### Post by srope01 on 2014-05-18
I just tried your solution and it worked. Thanks! I guess this one is solved (or at least there is a workaround as the bug still has to be fixed).

---

### Post by bapoumba on 2014-05-19
> **srope01 said:**
> I just tried your solution and it worked. Thanks! I guess this one is solved (or at least there is a workaround as the bug still has to be fixed).

You're welcome :)
Works for me too. Will add a comment to the bug thread and link back here.

---

### Post by ale-magnolo on 2014-05-22
light-locker gives me the impression to work but I can bypass it by pressing CTRL-ALT-F7 :-(
so in my opinion this thread should be marked as NOT SOLVED

---

### Post by bapoumba on 2014-05-22
> **ale-magnolo said:**
> light-locker gives me the impression to work but I can bypass it by pressing CTRL-ALT-F7 :-(
so in my opinion this thread should be marked as NOT SOLVED

That is strange. If I lock the screen and hit <ctrl><alt><F7> I get a message with a lock saying : This session is locked. you'll be directed to the unlock dialog automatically in a few seconds.
Which it does..

What do you have in your light-locker settings ?

---

### Post by ale-magnolo on 2014-05-22
I had the exact same settings as you, except for "lock on suspend" that was off, so I put it on but I still have the same problem of bypassing the lock with CTRL-ALT-F7.

I launch the locker with:
light-locker-command -l

The version I get with the -V param is:
light-locker-command 1.4.0

My system is Lubuntu 14.04 upgraded from a previous install, I think it was 13.10.

---

### Post by bapoumba on 2014-05-22
> **ale-magnolo said:**
> I had the exact same settings as you, except for "lock on suspend" that was off, so I put it on but I still have the same problem of bypassing the lock with CTRL-ALT-F7.

I launch the locker with:
light-locker-command -l

The version I get with the -V param is:
light-locker-command 1.4.0

My system is Lubuntu 14.04 upgraded from a previous install, I think it was 13.10.
Using** light-locker-command -l** also works for me, and I have the same version as you :
```
bapoumba@SonyBlue:~$ light-locker-command -V
light-locker-command 1.4.0
```

I fresh installed lubuntu 14.04 after having upgraded every release from 12.04.

---

### Post by srope01 on 2014-05-23
I temporarily removed the solved subject header. I also get the same as bapoumba. If I lock the screen and I hit CTRL-ALT-F7 then I get the "This session is locked" message.

I did a fresh install of Lubuntu. I tried an upgrade once, but there were so many problems afterwards, I just installed from scratch. But even with a fresh install, I am finding basic problems with 14.04. :-/

---

### Post by bapoumba on 2014-05-24
If it is working for you from a fresh install as it is working for me, I think that ale-magnolo's behavior may be linked to the upgrade that kept some user config. Now to find which one..

---

### Post by ale-magnolo on 2014-05-28
I have just tried once more and now it works as expected, no more bypass with CTRL-ALT-F7. Unfortunately I don't know what has changed... anyway I'm happy, and you can mark the thread as solved. Thank you.

---

### Post by bapoumba on 2014-05-28
That is srope01's thread, I'm sure they'll mark it as solved again next time they come back here :)
Glad to see it is working for you too now.

---

### Post by cikaRadule on 2014-05-29
nopasswdloginHi everybody. Found this thread while trying to solve my own problem with lock screen.
Not sure if we had the same problem, but maybe it will be helpfull to share the solution here...

I couldn't get my fresh 14.04 installed Ubuntu to lock itself using CTRL + ALT + L.
Thing worked for me is explained on this thread - [http://askubuntu.com/a/102222](http://askubuntu.com/a/102222)
Long story short - my user was added to nopasswdlogin group.

Hope it may help someone, either already on this thread or, as me, poor soul searching for a way to lock his screen :)

Cheers

---

### Post by bapoumba on 2014-05-29
@cikaRadule : I do not think this is the same issue, as yours was regarding a user having being set up to have no password at login while here we were talking about the screen not being locked when asked to. I cannot say for the other users from this thread, but my own user has never been in the nopasswdlogin group.

---

### Post by The Ratman on 2014-11-30
I found a simple solution which works for me.

The lock screen feature of Xubuntu 14.04 wouldn't work for me - either by clicking the padlock button in the Whisker Menu or with a keyboard shortcut.

I went to Settings > Light Locker Settings and set 'Enable light-locker' to ON (I decided to leave everything else at Never/OFF) and now I can lock the screen with the padlock button or with Ctrl-Alt-Delete.

---

