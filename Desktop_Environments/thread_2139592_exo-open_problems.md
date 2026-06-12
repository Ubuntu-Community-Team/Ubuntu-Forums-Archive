---
title: "exo-open problems"
date: 2013-04-27
forum: Desktop Environments
---

### Post by mreq on 2013-04-27
How does exo-open differ from xdg-open? I have some problems with it on both 12.04 and 13.04 xubuntu.

From time to time, some of exo-open or exo-helper processes hang and it causes my CPU to go crazy. The Xorg proccess jumps to ~30%, fan starts running and the temp rises from 45° to 75°. There's usually many of them spawned.

Are these problems xfce/xubuntu-specific, or would I encounter them in other DE as well? These problems make me consider dumping beloved XFCE for Unity.

---

### Post by Tamlynmac on 2013-04-28
exo-open is the tool from XFCE to open files etc in your preferred application.

xdg-open is a shell-script which works independent from the  desktop-environment. It will inspect your environment and if it can  detect that you are running Gnome, KDE, XFCE or LXDE it will use the  correct tool from your Desktop Environment.
If it can't detect your environment it will try to open the file itself.  So basically, if you know which Desktop Environment you are running,  you can use the tools which comes with your DE. If you're uncertain, or  you are writing a script which should work across different Desktop  Environments, use xdg-open.

This simple explanation is defined [here]("http://budts.be/weblog/2011/07/xdf-open-vs-exo-open").

My preferred choice is xdg-open, especially if your using apps and dependencies from different environments. If your going  to use [SIZE=2]exo-open to open a file, I suggest you define which app to open specific files with[/SIZE].  For a quick example, open a file with exo-open then in your file manager right click on the file and select  properties. Define which App to open the file (and similar files)  with. Then retry exo-open with the same file or similar file and I think you'll find it opens without any issue.

Hope this helps.

---

### Post by mreq on 2013-04-29
Thanks, that helped.

---

### Post by mreq on 2013-04-29
In case someone's exo processes hang like mine, I made a simple bash script to kill it ;) Add it to your $PATH and name it something like **kill_exo**. Afterwards, when you see CPU go crazy run it a couple times.

```

#!/bin/bash
pid=`pidof exo-helper-1`


if [[ $pid ]]; then
	kill -9 $pid
	echo 'Tried to kill one.'
else
	echo 'No exo-helper to kill.'
fi


exit 0

```

Improvements (possibly run it in some while loop over and over, till everything's killed) are welcome :)

---

