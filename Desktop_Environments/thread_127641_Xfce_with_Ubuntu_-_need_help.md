---
title: "Xfce with Ubuntu - need help"
date: 2006-02-09
forum: Desktop Environments
---

### Post by alfonz on 2006-02-09
Hi guys, sorry I wasn't sure where to post this

I just installed XFce on my Breezy box, and I love it, however I have one problem. I was trying to load Nautilus to use as a file manager but being clumsy that I always am, I did not use the --no-desktop commad. Long story short, Nautilus took over my xfce desktop and I have lost the right click usablility of xfce. Can anyone point me to the right direction how to restore that back...

On another note, is there a way to enable show icons on xfce desktop, and is there a way to completely remove the taskbar in xfce instead of just using autohide. 

If this is a somewhat of a double post, I will send my appologies right now but my search didn't come up with anything.

Thanks guys!


Update! Sorry guys, I have found a solution finaly :) posted [here]("http://www.ubuntuforums.org/showthread.php?t=102606&highlight=restore+xfce+desktop+nautilus")

Moderators, please feel free to earase this if you like.

---

### Post by closeyourwindows on 2006-02-09
is there a repository for this?  I was thinking about installing this as well and was wondering how well it worked.  how did  you install this, meaning what was the code you used to get it?  just curious.  I would like to try it out.  I am sure this is not the kind of help you were looking for.

---

### Post by syklitengutt on 2006-02-09
open nautilus trough terminal with this
nautilus --no-desktop

---

### Post by alfonz on 2006-02-09
[QUOTE=closeyourwindows]is there a repository for this?  I was thinking about installing this as well and was wondering how well it worked.  how did  you install this, meaning what was the code you used to get it?  just curious.  I would like to try it out.  I am sure this is not the kind of help you were looking for.[/QUOTE]

hmm its was easy, can't find the post that gave the instructions but is was basicaly this: 

add these repos to your /etc/apt/sources.list ... these basicaly updated my xfce install otherwise you will only get ubuntu's packages
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe
deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports-staging main universe
deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

then simply in terminal

```
sudo apt-get update
```
this might give you some error messages but that probably because of public keys or they are old repos don't worry

```
sudo apt-get install xubuntu-desktop
```
and restart x and choose xfce in sessions

Thats it! :)

---

### Post by alfonz on 2006-02-09
[QUOTE=syklitengutt]open nautilus trough terminal with this
nautilus --no-desktop[/QUOTE]


yeah that was what I typed or so I thought but it ended up being nautilus --no-destop , :( one letter got to me ha 

Thanks for the reply though.

---

