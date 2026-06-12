---
title: "PCMANFM 1.2 - Open as Root"
date: 2014-03-05
forum: Desktop Environments
---

### Post by Viriatu on 2014-03-05
Greetings all...

I notice that the option to open files and folders 'as root' is no longer available in the new pcmanfm 1.2 version.
Can anyone tell me if there's a simple way to bring this function back?

Regards...
Edd

---

### Post by sudodus on 2014-03-05
Welcome to the Ubuntu Forums :-)

It is risky to stay in an environment with root privileges. It is better to perform single commands with sudo (and be reminded that they are powerful and potentially risky).

It is possible to launch pcmanfm from a terminal window with

```
gksudo pcmanfm
```

and get root permissions, but I do *not* recommend it.

---

### Post by Lars Noodén on 2014-03-05
To refine that a little, it is less unsafe to launch it with [gksudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo) since it is a graphical program.

I'm pretty sure that built in function is quite gone.  There was some discussion about removing it and the reasons for doing so, which could probably be tracked down in the mailing lists.  But it was removed deliberately.  Maybe if PCManFM supports plug-ins one of the plug-ins might restore that functionality, but in the mean time there is gksudo.

---

### Post by ajgreeny on 2014-03-05
Like Viriatu I find this missing option a bit annoying as it is still available in other file managers, either as scripts (nautilus), or using custom actions (thunar).  I don't know about any kde options to do the same.

Perhaps I am wrong but I think we are all aware that it is possible to do great damage to your system when using a root file manager, and to warn against that there was a large red warning banner at the top of the pcmanfm window.  As you say, it is still possible to open the file manager as root using ```
gksudo pcmanfm
``` and I have made a launcher for that in my VBox install of Lubuntu 14.04 and put it in the autohidden panel I have on the left of the screen, a bit like the unity launchbar, but much less resource hungry, however doing it that way gives you no warning of the manner in which the manager is open.

---

### Post by Rob Sayer on 2014-03-05
I too find this annoying.  My standard solution would be to just use dolphin, which is my favorite file manager.

Unfortunately, I can only run dolphin from a terminal in lubuntu 13.10.  The fix I've found here and on askubuntu seems to be making it the default in lxsession from preferences.  However, it's not working for me and I'm not getting much response on that.  Lubuntu support definitely lags other ubuntu desktop versions.

I'm thinking of reinstalling kubuntu at this point ....

---

### Post by Lars Noodén on 2014-03-05
Rob, if you've filed a bug for Lubutu, post it here and we can add our 'me, too' to it.  Lubuntu is great in many respects but it seems not to be able to accept any other default file manager besides PCManFM.  Adding Thunar or Dolphin seems to have no effect even when the settings are changed.

---

### Post by walterorlin on 2014-03-16
Actaully PCmanfm does tell you if you are logged in as root there is a ! to the left of the new tab button.

---

### Post by vasa1 on 2014-04-20
Instructions (*caveat emptor*) are here: [http://wiki.lxde.org/en/PCManFM](http://wiki.lxde.org/en/PCManFM)

---

### Post by Charlotte18 on 2014-04-28
I'm curious to know whether those of you warning about the dangers of opening a folder in the gui as root have some current examples of those dangers from your own experience. Personally, I've never suffered from those dangers. So what has happened to you lately that makes you warn the rest of us?

---

### Post by Dennis N on 2014-04-28
The built-in as default function to open as root is gone, but PCManFM 1.2 supports custom actions. One of those offered on the Lubuntu blog does exactly that: open a folder as root. After the script is installed, right-click on the folder, and the option is there in the right-click menu.

Download the custom action script to open folder as root from here:

[http://lubuntublog.blogspot.com/p/actions_24.html](http://lubuntublog.blogspot.com/p/actions_24.html)

I installed it to try, and it works.

If you follow the link to MadeBits Blog there are more custom actions.

---

### Post by vasa1 on 2014-04-28
> **Charlotte18 said:**
> I'm curious to know whether those of you warning about the dangers of opening a folder in the gui as root have some current examples of those dangers from your own experience. Personally, I've never suffered from those dangers. So what has happened to you lately that makes you warn the rest of us?
Nothing happened to me but I understand the thinking behind the removal and approve of it being made available (for those who really want it). It's not really necessary to experience a calamity to appreciate its potential :) 

[https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002909.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002909.html)
[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1290101](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1290101)

---

### Post by bapoumba on 2014-04-29
> **Charlotte18 said:**
> I'm curious to know whether those of you warning about the dangers of opening a folder in the gui as root have some current examples of those dangers from your own experience. Personally, I've never suffered from those dangers. So what has happened to you lately that makes you warn the rest of us?

> **vasa1 said:**
> Nothing happened to me but I understand the thinking behind the removal and approve of it being made available (for those who really want it). It's not really necessary to experience a calamity to appreciate its potential :) 

[https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002909.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002909.html)
[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1290101](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1290101)

+1 to vasa, and also maybe because you are not the only one reading the forums ?

---

### Post by ibjsb4 on 2014-04-29
> **Dennis N said:**
> The built-in as default function to open as root is gone, but PCManFM 1.2 supports custom actions. One of those offered on the Lubuntu blog does exactly that: open a folder as root. After the script is installed, right-click on the folder, and the option is there in the right-click menu.

Download the custom action script to open folder as root from here:

[http://lubuntublog.blogspot.com/p/actions_24.html](http://lubuntublog.blogspot.com/p/actions_24.html)

I installed it to try, and it works.

If you follow the link to MadeBits Blog there are more custom actions.

Its a handy tool for the experience user, thanks for the link :)

---

