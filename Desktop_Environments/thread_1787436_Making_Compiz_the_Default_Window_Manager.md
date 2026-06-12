---
title: "Making Compiz the Default Window Manager"
date: 2011-06-21
forum: Desktop Environments
---

### Post by charliewhizbeez on 2011-06-21
Hey all, I'm thinking about switching from Ubuntu 11.04 classic to Xubuntu 11.04.  My main priority is to have compiz running.

However, though I know how to get it running, I want to be able to use it without using the 
```
compiz --replace 
``` code every startup.

I know how to make it default in GNOME, however not in XFCE.

If you can help, that'd be great.

Thanks!!

---

### Post by nzjethro on 2011-06-21
Hey, I'm having the same issue in 10.10 with Xfce. Try adding

```
compiz --replace
```

to your list of start-up commands (Settings > Session and Startup > Application Autostart). This seems to solve the issue for me 2 times out of 3, but I'll eagerly watch this forum to try and find any further ideas.

---

### Post by 3Miro on 2011-06-21
Start terminal and run "compiz --replace" (Alt + F2).

With compiz running, go to Menu -> Settings -> Sessions and Startup. Then go to Session tab and and save session.

---

### Post by charliewhizbeez on 2011-06-21
Yeah.  I already know about all of those solutions.

I was talking about something more like [http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/#comment-4975]("http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/#comment-4975")

> The more-difficult-but-better way

Update: Reportedly this way doesn’t work anymore in Xubuntu 9.04 and above, due to the new version of Xfce being used (namely version 4.6). Though I haven’t verified them myself, sisco311 provides updated instructions in the comments section. Users of Xubuntu 9.10 reportedly need Sahkolihaa’s instructions.

So… You prefer the scary stuff? Well, it’s not that difficult, actually. You just press Alt+F2 and enter

gksudo "mousepad /etc/xdg/xfce4-session/xfce4-session.rc"

Basically, that opens the file xfce4-session.rc with root rights with the text editor mousepad.

In this file, all you have to do is replace:

Client0_Command=xfwm4

…with:

Client0_Command=compiz

(Thank Ubuntuforums user sisco311 for this one)

Do note that this makes Compiz default for all users, as opposed to the previous method which made it default just for you.


But for 11.04.  7.04 was a long time ago

---

### Post by FormatSeize on 2011-06-21
> **charliewhizbeez said:**
> Yeah. I already know about all of those solutions.
 
I was talking about something more like [http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/#comment-4975](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/#comment-4975)

You are looking for something like [this](https://wiki.archlinux.org/index.php/Compiz#Autostart_.28without_.22fusion-icon.22.29_.28Preferred_Method.29)?

---

### Post by nzjethro on 2011-06-21
> **FormatSeize said:**
> You are looking for something like [this](https://wiki.archlinux.org/index.php/Compiz#Autostart_.28without_.22fusion-icon.22.29_.28Preferred_Method.29)?

Hey this worked for me perfectly. Thanks.

---

### Post by charliewhizbeez on 2011-06-22
Thanks for that solution.  Haven't been able to try it, as I'm on vacation without my Xubuntu laptop.  Thanks!!!

---

