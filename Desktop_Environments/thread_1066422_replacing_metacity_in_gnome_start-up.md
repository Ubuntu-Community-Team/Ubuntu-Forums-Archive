---
title: "replacing metacity in gnome start-up"
date: 2009-02-10
forum: Desktop Environments
---

### Post by malachi1990 on 2009-02-10
With e16, you have the option of starting e16 within gnome or kde, which essentially starts up e16 then starts gnome/kde on top of it before shutting down the default wm (metacity/kwin).  What I want to know is if there is a way to configure gnome to start up with e16 simultaneously (to decrease start up time).

Thanks for any help.

---

### Post by carrett on 2009-02-10
All you gotta do is edit the file ~/.gnomerc and add a line like this:

```
export WINDOW_MANAGER=/usr/bin/e16
```

If /usr/bin/e16 isn't the path to the executable for the e16 window manager, then replace it with the proper path. After you're done editing, log out, log back in, and voila it should work.

---

### Post by malachi1990 on 2009-02-10
I don't have ~/.gnomerc, but I do have what is apparently a link to /etc/X11/Xsession.d which covers gnome, I think.  Is this what I'm looking for?

BTW, what does the rc stand for?

---

### Post by carrett on 2009-02-10
Create a .gnomerc.

```
touch ~/.gnomerc
```

---

### Post by malachi1990 on 2009-02-11
Thanks!

---

### Post by jenkinbr on 2009-02-11
Will this work for emreald too.

I currently have the command ```
emerald --replace
``` in my sessions startup.

If I added the line ```
export WINDOW_MANAGER=/usr/bin/emerald
```, would that work the same as the e16 varient above?

---

### Post by carrett on 2009-02-11
@[jenkinbr]("http://ubuntuforums.org/member.php?u=446630")  			 Only one way to know....

---

### Post by jenkinbr on 2009-02-11
I'll give it a try later - if it works, great, if it doesn't, oh well, if it breaks something, there's alwasy tty1 to nano .gnomerc

---

### Post by carrett on 2009-02-11
@jenkinbr I don't know what emerald is exactly, I've never used it. If it is a window manager, you should be fine. Glad to know you know about the VCs though if you can't use your GNOME session for some weird reason. You could also just log in using a different session than the GNOME one since that'd be all you're breaking.

---

### Post by jenkinbr on 2009-02-11
> **carrett said:**
> @jenkinbr I don't know what emerald is exactly, I've never used it. If it is a window manager, you should be fine. Glad to know you know about the VCs though if you can't use your GNOME session for some weird reason. You could also just log in using a different session than the GNOME one since that'd be all you're breaking.

Emerald is actually a window decorator.

Doing a bit of research on this, Compiz-fusion appears to be the window manager, while I use emerald as a decorator.  However, these terms seem to be used loosely in reference to each other, so I will probalbly backup my .gnomerc (if it exists, and try this.

Good point about logging in with a different session.  I could use LXDE to log in, but I find the VC's easier to use for a quick rm and mv command.

---

### Post by zika on 2009-02-11
guys thank You for enlightening discussion. I've just went to sysv-rc-conf, un-X-ed  gdm and regained control of many things ... ;) great stuff!

**update:**  there is one downside of removing gdm out of the loop. if I remove it and boot from CLI with *startx*  then in that X-session I cannot access my USB flash drives that are connected aterwards and I cannot open the ntfs partition that Vista resides on. if bring back gdm in I sysv-rc-conf everything is as it used to be. so, beware, ... I will have to wight pro's and con's ... ;) yes, I know, You all wanted to put another windows manager in the loop and I am trying to get out all the window managers out of it ... :)

---

### Post by malachi1990 on 2009-02-11
Yes, this will work with other window managers.  Fluxbox works pretty well, as it has no compositing like e16 (which destroys tge frame rate on 2d games :( ).

---

### Post by jenkinbr on 2009-02-12
Note:  I tryed adding ```
export WINDOW_MANAGER=/usr/bin/emerald
``` to my ~/.gnomerc, but after restarting X, I was left without compiz and couln't access the menus or anything.  (Alt+F2 didn't work either)  Thankfully, I had an undecorated terminal window sitting on my desktop, so I was able to rm ~/.gnomerc (I had to create it) and then CTRL+ALT+BACKSPACE to restart X

In conclusion, don't try replacing your window manager with emerald.  Bad Idea, and most users don't have the luxury of a terminal window on the desktop. (in case you are wondering, it looks like [this..]("http://ubuntuforums.org/attachment.php?attachmentid=102801&d=1234233141"))

---

### Post by carrett on 2009-02-12
@jenkinbr: Too bad. I tried it with BlackBox and it worked out just fine. I guess emerald does somethin' funky.

@zika: What does automounting these days? I thought it was gnome-volume-manager, but I don't have that package installed and my drives automount fine. Whatever it is, it needs to be running. The best guess I can come up with is /usr/lib/gvfs/gvfs-hal-volume-monitor.

---

### Post by zika on 2009-02-12
> **carrett said:**
> @zika: What does automounting these days? I thought it was gnome-volume-manager, but I don't have that package installed and my drives automount fine. Whatever it is, it needs to be running. The best guess I can come up with is /usr/lib/gvfs/gvfs-hal-volume-monitor.
no, that did not give me auto-mounting. never mind, excluding gdm from the loop did not give me visible speed improvement so I'll leave it be. nice experiment though in which I've learned a lot, what was the main purpose of it. the thing that everything is still working is added bonus ...;) [http://ubuntuforums.org/showpost.php?p=6722601&postcount=29](http://ubuntuforums.org/showpost.php?p=6722601&postcount=29)

---

### Post by jenkinbr on 2009-02-12
> **carrett said:**
> @jenkinbr: Too bad. I tried it with BlackBox and it worked out just fine. I guess emerald does somethin' funky.

Technically, emerald is only a window *decorator,* and not a window manager.  Metacity is apparently both, and Compiz-Fusion is a window manager only (abeit a very fun one ;))

[size=1]I could be wrong in my statement, I have very little knowledge in the area...[/size]

---

