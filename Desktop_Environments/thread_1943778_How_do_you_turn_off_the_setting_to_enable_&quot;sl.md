---
title: "How do you turn off the setting to enable &quot;slow keys&quot; whenever you hold down shift?"
date: 2012-03-20
forum: Desktop Environments
---

### Post by joehill on 2012-03-20
I've always said that one of the things that drives me crazy about using people's Windows machines is that whenever I hold down the shift key I get that message saying "Sticky keys have been enabled" then have to go into settings to turn it off, but at least Windows gives you an obvious way to turn off this preference so it doesn't happen in the future.

I just switched to xfce because unity runs like a slug on my system, and every 10 minutes or so I hold down the shift key then have to go into the accessibility settings and toggle on and off the "slow keys" setting. There's no clear way to tell XFCE I NEVER want slow or sticky keys so stop turning it on automatically. I just happen to like holding down the shift key when I'm trying to think of what word to start my sentence with. I've carefully checked all the system settings and done many searches on Google and if that doesn't turn up a solution clearly there's something wrong with the interface.

Is there a setting for this, or do I just have to live with my computer thinking I have a degenerative nervous disease every 10 minutes?

---

### Post by Rodney9 on 2012-03-20
That sounds strange, I sat here for a minute holding shift and slow keys is still turned off on my Xubuntu 11.10

You haven't got a keyboard shortcut set ?

Rodney

---

### Post by joehill on 2012-03-20
Nope, as someone who has always hated these illogical default settings, I'm the last person who would go and set that as a keyboard setting. I should mention I'm using Precise, so this could be a new feature they've introduced to be more Windows-like.

---

### Post by *uu on 2012-06-06
I think I might have the same issue: Suddenly and sporadically, key strokes get registered only when I hold them for a rather long time. This seems to affect *all* keys. I can't confirm that it is being caused by holding the Shift key; I don't know what key turns this on, and couldn't reproduce it now when I tried to. But as Joehill described, I have to go to the accessibility settings and enable and re-disable (the setting is *not* checked when the issue occurs) 'Slow Keys' to get my normal keyboard back.

Did you ever find a cure, Joehill? Or anybody else for that matter?

I'm on Ubuntu 12.04 Precise with Unity, Gnome-Shell and Mate Desktop also still installed, but now with XFCE4 and Compiz as my default desktop. XFCE4 is at version 4.10.0 right now.

Any hints on this? :)


EDIT: Looks like it is indeed the Shift key being held down a bit longer that turns this on — occasionally, but not always!

---

### Post by tepples on 2012-06-22
Google [ubuntu precise slow keys  ] led me to
[http://ubuntuguide.org/wiki/Ubuntu_Precise_Tips#Turn_off_Hot_Keys](http://ubuntuguide.org/wiki/Ubuntu_Precise_Tips#Turn_off_Hot_Keys)

Menu > System > Administration > Accessibility > Activation Gestures > Turn OFF gestures

I haven't found a corresponding setting in Xubuntu, but to ease the pain in case you do activate it by accident, try reducing the acceptance delay:

Menu > Settings > Settings Manager > Accessibility > Keyboard > Slow Keys > Acceptance delay

---

### Post by stinkeye on 2012-06-23
Try the dconf settings.

Turn off stickykeys and slowkeys.
```
gsettings set org.gnome.desktop.a11y.keyboard stickykeys-enable false
gsettings set org.gnome.desktop.a11y.keyboard slowkeys-enable false
```

Disable accessibility keyboard shortcuts
```
gsettings set org.gnome.desktop.a11y.keyboard enable false
```

---

### Post by *uu on 2012-06-29
tepples, stinkeye, thank you both for your suggestions. Unfortunately, they don't work for me, as this issue is occurring in XFCE, and these Gnome and/or Unity settings are either not available, or have no effect.

I did find a very weird way to get around this issue, which recurs with every new XFCE session. On my search for a usable desktop environment, I also installed MATE on the way. I'm not using it by now, but it is still installed.

Now, whenever this issue is back, I can solve it by starting 'mate-control-center' and there opening 'Assistive Technologies' > 'Keyboard Accessibility'. Opening this window alone (everything in there is unchecked) will stop my desktop from activating Sticky Keys or Slow Keys completely, Apparently it disables the Assistive Technologies or at least their hotkey activation feature completely -- well, at least until I log out and back in, and thereby start a new XFCE login session.

This is, of course, not a really good way to deal with the issue, but it is the only way that I found to work for now.

I even uninstalled the MATE Desktop Environment completely, as I suspected it to be the cause behind the hotkey activation altogether. But the issue remained, and it left me without any way to deal with it. So I had to re-install MATE.

Does anybody have any helpful ideas on this? Especially, why the MATE Control Center can switch this off, while Gnome or Unity settings don't seem to have any effect on the XFCE session? I also tried de-installing several packages I could identify to have to do with those assistive technologies, but most of them are dependencies of one of the desktop environment, and hence want to remove the DE with them... Seems like something is really messed up bad there...

---

### Post by *uu on 2012-07-10
Upon further investigation, I came across several forum posts and bug reports concerning this issue throughout distros that use XFCE or even on the XFCE websites. This issue seems to occur only for XFCE users that log on to their XFCE session using the GDM login manager. Apparently, it is a new bug in either GNOME_SETTINGS_DAEMON or XFCE or Xserver itself that causes accessX related settings or parts of it to be turned on upon login.

There are several suggestions around on how to fix the issue, as well as patches and bugfixes. What I found out that worked for me was a little command line program called 'xkbset'. It is available via the package manager.

After a freshly started XFCE session, xkbset displays the following current settings:
```
$ xkbset q
[...]
Accessibility Features (AccessX) = On
[...]
```

It can be turned off:
```
$ xkbset -a
```

This will immediately turn off the accidental triggering Slow Keys and Sticky Keys by holding (more than 6 to 10 seconds) or pressing Shift key (5 times in rapid succession), hence solve – well, rather circumvent – the issue. I now have this command run automatically on session startup.

I hope this might help someone else, as well. :)


Just for future reference, here is a list of the sources that I run across:
[LIST]
[*][https://bugzilla.redhat.com/show_bug.cgi?id=816764](https://bugzilla.redhat.com/show_bug.cgi?id=816764)
[*][https://bbs.archlinux.org/viewtopic.php?id=142721](https://bbs.archlinux.org/viewtopic.php?id=142721)
[*][http://www.math.missouri.edu/~stephen/software/#xkbset](http://www.math.missouri.edu/~stephen/software/#xkbset)
[*][http://forums.fedoraforum.org/showthread.php?t=277298](http://forums.fedoraforum.org/showthread.php?t=277298)
[*][https://bbs.archlinux.org/viewtopic.php?pid=1112061](https://bbs.archlinux.org/viewtopic.php?pid=1112061)
[/LIST]

---

