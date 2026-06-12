---
title: "KDE 4.1 Plasmoids"
date: 2008-08-02
forum: Desktop Environments
---

### Post by wookietim on 2008-08-02
Does anyone have any idea how to use these things? I try to click on "Add Widgets" and get a list. If I try to actually add one from that list, I get a tiny little black dot on my desktop that does exactly nothing... when I try to "Install from the web" I find ones I would like to use and click on "Install" and all that happens is the button changes it's text to "Uninstall"... is it just me or do Plasmoids simply not work?

---

### Post by sayakb on 2008-08-03
Just click on Add Widgets and drag and drop the widget to your desktop/panel.

---

### Post by GeneralZod on 2008-08-03
Web ones do not work at the moment, although this is largely a server-side issue: the server does not discriminate between "native" Plasmoids (compiled binaries) which wouldn't work reliably anyway (native code is not cross-platform) and definitely *shouldn't* be allowed to run; and scripted Plasmoids, such as those written in Python, Ruby or QtScript.

I'm not sure what the state of the script interpreters is at the moment: if they're not up to scratch, then this feature probably shouldn't have been included with 4.1, IMO.

---

### Post by utkjamie on 2008-11-04
How do I uninstall Plasmoids? I installed a few OS X widgets and none display properly so I want to just remove them from my system. Suggestions?

---

### Post by drumz on 2008-11-04
If you upgraded from a previous version of Ubuntu (8.04 in my case), I had problems getting plasmoids to display.  Taking the advice of another poster I logged out, hit ctrl-alt-f1 to log in from a command line prompt, moved my .kde and .kderc directories into another directory ('old' in my case) logged out of the command line, hit ctrl-alt-f7 to switch back to the gui and then logged in.

After that adding/removing plasmoids worked much better but still wasn't perfect.  (I've noticed that sometimes the GUI seems sluggish at times which may be the problem (not being patient enough).)

As someone else pointed out, there's not a lot of plasmoids currently available under Kubuntu right now although if you go up to [www.kde-look.org](www.kde-look.org) there are a lot.

---

### Post by utkjamie on 2008-11-28
Has anyone figured out how to uninstall plasmoids? I tried installing a few Mac OS widgets and none of them happen to work. They show up in my list of plasmoids to add and I'd like to get rid of them.

---

### Post by ziogelis77 on 2008-12-03
> **utkjamie said:**
> Has anyone figured out how to uninstall plasmoids? I tried installing a few Mac OS widgets and none of them happen to work. They show up in my list of plasmoids to add and I'd like to get rid of them.

There is no simple way to do that, imho. But it could be done this way (I assume they are added using the add widgets menu):

Lets say I installed widget system_monitor2 which is actually a superkaramba theme.

Go to /home/YourUserName/.kde/share/apps/plasma/plasmoids/

You will find a folder sk_system_monitor2 - delete it. 

Now go to

/home/YourUserName/.kde/share/kde4/services 

And remove the *.desktop file for the theme:

plasma-applet-sk_system_monitor2.desktop


and your plasma menu list is clean. Just make sure you have not made any serious modifications to your desktop/plasma before that, as after you do these things plasma will likely crash, then restart, and all your artwork will be lost :)

---

### Post by utkjamie on 2008-12-07
> **ziogelis77 said:**
> There is no simple way to do that, imho. But it could be done this way (I assume they are added using the add widgets menu)...

Ah, that did the trick. Thanks!

Now let's hope that KDE 4.2 has a cleaner way to do this.

---

### Post by revertex on 2009-04-21
This isn't the best way to remove plasmoids.

```
plasmapkg --list
```

to find the name of plasmoid you want to remove

```
plasmapkg --remove name-of-plasmoid-you-want-to-remove
```

i know this thread is old, but maybe it should help other people in a future.

```
plasmapkg --help
``` for more info

---

### Post by rsk02 on 2009-06-04
Thank you Revertex.

---

