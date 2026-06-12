---
title: "Need the name of a program or package"
date: 2009-04-05
forum: Desktop Environments
---

### Post by Ouia on 2009-04-05
About a week ago I installed a program using add/remove option to change the look of ubuntu.
It worked just fine after that, so I know it looks like this:

[http://xs.to/xs.php?h=xs231&d=08391&f=gtk-chtheme-aud-default-820.jpg](http://xs.to/xs.php?h=xs231&d=08391&f=gtk-chtheme-aud-default-820.jpg) 

However, when I started my computer the next day I couldnt log in anymore, because of what seem to be driver problems of my graphicscard.

see thread:
[http://ubuntuforums.org/showthread.php?t=1113308&page=2&highlight=yellow+white+square](http://ubuntuforums.org/showthread.php?t=1113308&page=2&highlight=yellow+white+square)

So now I want to remove that program that I installed, but I dont exactly how it's called.
I can only assume that it is called GTK+ 2.0 Change Theme, but I'm not sure whether this is right or not.

I've already tried ```
apt-get remove gtk-chtheme
``` but with not much luck.

So my question is of anyone knows how the program or package is called that I should remove

If I remember correctly, I found searching for 'theme' in 'add/remove programs' and it was for gtk.2
I also think it was rated 3 stars. It had a gnome foot and a red sign.

Thanks in advance

---

### Post by drs305 on 2009-04-05
You can look at various log files. See if you recognize anything from this list. The "tail" portion of the command lets you hold down the ENTER key to scroll through the list. Use the "q" key to exit. Omitting that portion will scroll all the way to the end, where your install probably is located.

```

sudo cat /var/log/dpkg.log | grep installed | grep -v 'half-installed'  # scrolls all the way to end
sudo cat /var/log/dpkg.log | grep 'installed' | grep -v 'half-installed' | less  # starts at beginning

```

---

### Post by bigbencg on 2009-04-05
If I would have read the first post closer, I wouldn't have said the same thing.

---

### Post by skullmunky on 2009-04-05
You can also see the logs of packages you've installed in Synaptic:

File->History

I use this all the time, because I like to go on package installing sprees in synaptic, browsing for fun looking new apps and installing.  Then I forget what I've just installed, so the history helps with that.

If you can't log in to a normal desktop session, you can still sometimes get Synaptic up and running by logging into a Failsafe session, and running synaptic from a terminal.

---

### Post by Ouia on 2009-04-06
Good old pen and paper ;)

I now know it was actually GTK-chtheme 0.3.1-2

I must have deleted it because I can't delete it again.


[HTML]If you can't log in to a normal desktop session, you can still sometimes get Synaptic up and running by logging into a Failsafe session, and running synaptic from a terminal.[/HTML]

I can't get into anything but the failsafe terminal.
Which accidently looks suspiciously similar to the point where the computer stalls. (yellow background with white square)
Accept in the stalled version I can't type anything

---

### Post by Ouia on 2009-04-06
Problem solved.

It was a gnome problem.

I ran rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Than I reinstalled the driver and now it's up and running again.

I will have to redo all the pimpings to my looks though.:p

---

### Post by drs305 on 2009-04-06
At least for your panels, once you have them set the way you want you can save them with the following. Choose your own *path/filename*:
```

*To save:*
gconftool-2 --dump /apps/panel > ~/Desktop/*panel_settings*
*To restore:*
gconftool-2 --load ~/Desktop/*panel_settings* && killall gnome-panel

```

---

