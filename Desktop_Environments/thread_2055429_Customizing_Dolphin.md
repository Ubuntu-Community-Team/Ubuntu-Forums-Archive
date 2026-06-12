---
title: "Customizing Dolphin"
date: 2012-09-09
forum: Desktop Environments
---

### Post by dargaud on 2012-09-09
Hello all,
I'd like to customize the Dolphin file manager so that a script is called when a key is pressed. And that the script receives the currently selected files as parameters. How would I go to do this ?
I don't want the long-wided route of doing right-click, open with, select, etc, I want a one key solution.
Thanks.

---

### Post by Epodx64 on 2012-09-09
Have you tried going (in dolphin) to control configure shortcuts?

---

### Post by dargaud on 2012-09-09
Well, I see the option to add a new scheme, but I don't see how to add a new script or key. Maybe I'm missing something.

---

### Post by Epodx64 on 2012-09-10
I don't really see any option to add a script but maybe you could add the script to the config file 

sudo nano /home/ryanepod/.kde/share/config/dolphinrc

or maybe you could setup a script to run in the background at startup

---

### Post by dargaud on 2012-09-10
I don't see a place to add custom actions in the config file...

---

### Post by dargaud on 2012-09-11
OK, I found part of the solution [here]("http://devel.pc-serwis.com/2010/02/how-to-add-service-menu-entry-in-dolphin/"). I wrote a file /usr/share/kde4/services/ServiceMenus/DelSameExt.desktop:
```
[Desktop Entry]
Actions=delSameExt
Encoding=UTF-8
ServiceTypes=KonqPopupMenu/Plugin,all/allfiles
ExcludeServiceTypes=kdedevice/*,inode/directory
Type=Service

[Desktop Action delSameExt]
Name=Delete this and all files that have the same extension
Icon=/usr/share/icons/oxygen/48x48/actions/edit-delete-shred.png

#Exec=a.sh -compose “attachment=file:/$(echo %F | sed ‘s/\\ \\//,file:\\/\\//g’)”
# bactick operator also works
Exec=~/bin/DelSameExt.sh %F
```

and a script ~/bin/DelSameExt.sh that starts with something like this:
```
#! /bin/sh
# This needs: sudo aptitude install trash-cli
date >>/tmp/DelSameExt.log
echo trash-put -v "$@" >>/tmp/DelSameExt.log
```

Now all I need to do is, finish the script and figure out a way to have this desktop action called when I press a chosen key. Will post here if I figure it out.

---

### Post by dargaud on 2012-09-12
Keep replying to myself, akin to thinking out loud... Anybody knows how to add shortcut keys to service actions in Dolphin ? The two seem separate: there's no service/action in the shortcut list and there's no way to add a shortcut key to an existing service.

---

