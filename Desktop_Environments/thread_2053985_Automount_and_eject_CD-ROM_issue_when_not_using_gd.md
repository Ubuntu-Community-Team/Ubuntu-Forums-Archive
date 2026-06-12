---
title: "Automount and eject CD-ROM issue when not using gdm"
date: 2012-09-06
forum: Desktop Environments
---

### Post by digitalnome on 2012-09-06
The basic problem is that the automount (and eject) of cd-rom (and I presume USB devices) have stopped working when in X after disabling the graphical login gdm in favour of the standard text based console login.

Warning! I am fairly new to all this ... 

**_Details_**

I have set up a new Linux box using the Ubuntu 12.04 minimum install ISO I installed Xorg, xfce and gdm. This setup worked fine no problems.

Later I decided that I wanted to _get rid_ of the graphical login screen so I disabled **gdm**

```
echo "manual" | sudo tee -a /etc/init/gdm.override
```

I then set up a new .xinitrc in my profile

```
exec ck-launch-session dbus-launch startxfce4

```

[I]On a side note, I have also tried.... 

```
exec ck-launch-session dbus-launch startxfce4
```
,
```
exec ck-launch-session startxfce4
```
and
```
exec startxfce4 --with-ck-launch
```
[/I]

Added user to group..

```
plugdev
```

as some suggested this could be an issue.

**_Problem_**

The problem that I am experiencing is that ever since I disabled gdm the **cd-rom automount (and eject)** no longer work when in X. Tried with xfce's thunar volume manager and pacmanfm.

error:
> Not Autherised

Reading though various forums I came to the conclusion that the problem isn't specific to xfce's thunar volume manager plug or pcmanfm and is rather something to do with the underlying authorisation system used for such procedures when logged in as an standard user. Removing gdm has some how broken this so a user doesn't have permission to mount/unmount the device and filing system automatically.

After more reading I came cross **consolekit and policykit** which  should be responsible in allowing this authorisation for system users.. bingo!

I came to the new conclusion that when starting X from logging in via the console (logind ?) that the functionality of gdm and polkit-gnome wasn't being fully replicated.

From what I can gather **pam_ck_connector.so** as a part of pam.d is used when logging in via the console login to create a session for the user?

**[Update]**

One thing I did notice when using the following command before and after  starting X. 

```
ck-list-sessions
```

was when using gdm the sessions "active" field would remain "True".

 However,  when not using gdm it would be "True" after logging in then once I had started X the session would then show as "False". 

This session active field obviously has something to do with the problem?

Also noticed that if I started X as sedo that the problem would go away further highlighting this session issue.

_Question_

How can I fix this so that I can log in as a standard user via a text based console login screen, type startx and still have the automount functionality? 

I am sure there are solutions that can side step the cd-rom problem, however, I would rather  solve the above as I can see potential problems further down the road as a result.

Many thanks if you got this far  ;) ... I tried to provide as much info as possible,

---

