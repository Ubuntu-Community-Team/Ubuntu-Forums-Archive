---
title: "How do we auto-hide the top menu of the default Ubuntu 13.10 desktop?"
date: 2014-01-25
forum: Desktop Environments
---

### Post by Damico on 2014-01-25
I've easily enabled the auto-hide feature of the side launcher, so, now I just need to enable the auto-hide feature of the top menu.

But how?

---

### Post by vasa1 on 2014-01-25
Why don't you just use a more appropriate distro? Or do you have some other motive?

---

### Post by Damico on 2014-01-25
> **vasa1 said:**
> Why don't you just use a more appropriate distro? Or do you have some other motive?

I appreciate the response, but I don't understand the question.
I asked my friends what Linux distro to use for a basic desktop user, and they said Ubuntu. 
So, I installed the latest Ubuntu.
I'm a basic Linux user.
I have the same needs everyone else has, which, for example, is why I seal my envelopes before I put them in the snail mail, just like everyone else does.
But, this doesn't need to be a privacy question.

It's simply a question of how to set the top menu to auto hide.

I'll ask in the desktop section.
So, is there a way to delete this entire thread?

---

### Post by coffeecat on 2014-01-25
*Thread moved to **Desktop Environments**.*

As you've edited out your privacy concerns from the OP, I've moved the thread for you. You can't delete threads/posts; we don't unless they contravene the Code of Conduct. If you want a thread of yours closed or moved, you can use the report post button in your own post to send a request to the staff area.

---

### Post by ibjsb4 on 2014-01-25
A "more appropriate distro" meaning one with a desktop environment that can be more easily changed to your needs.

I also am a basic desktop user and find gnome-classic desktop meets my needs (and the panels will auto-hide).  It can be added to your current install.

[https://apps.ubuntu.com/cat/applications/saucy/gnome-panel/](https://apps.ubuntu.com/cat/applications/saucy/gnome-panel/)

Then reboot and when you get to your login window click on the icon in that window and choose your desktop environment (try no-effects).

---

### Post by buzzingrobot on 2014-01-25
> **Damico said:**
> I've easily enabled the auto-hide feature of the side launcher, so, now I just need to enable the auto-hide feature of the top menu.

But how?

The top panel in Unity, the default Ubuntu interface, is not intended to be hidden.

Several other interfaces are available for Ubuntu: Same underlying code and system, different GUI on top.  To start, here's Xubuntu: [http://xubuntu.org](http://xubuntu.org); here's Lubuntu: [http://lubuntu.net](http://lubuntu.net); and here is Kubuntu:  [http://kubuntu.org](http://kubuntu.org).  

Another popular interface is the Mate desktop:  [http://mate-desktop.org/](http://mate-desktop.org/). There are instructions there for installation on Ubuntu.  Mate is also used by the popular Linux Mint distribution ([http://linuxmint.com](http://linuxmint.com)), which is also built on a Ubuntu base.  Linux Mint also offers its own Cinnamon interface.

I believe each of those interfaces allow panels to be, optionally, hidden. Live images are available for each, meaning that you can burn an image to DVD or a USB stick, boot it, run it and check it out, without interfering with the system that is installed on your machine. (Will run slower, though, espcially off a DVD.)

All of these interfaces are also available on many other Linux distributions.  The advantage of using something based on Ubuntu (known as an "Ubuntu derivative") is that you get access to the software in Ubuntu's repositories, the same support for multimedia, and the same quality of font rendering on screen.

---

### Post by philinux on 2014-01-25
Expanding on what buzzingrobot said, the top panel is not only the indicator panel it is also the global menu bar. It cannot autohide. 

Here's some background to it. [https://wiki.ubuntu.com/MenuBar](https://wiki.ubuntu.com/MenuBar)

---

### Post by Damico on 2014-01-27
> **philinux said:**
>  It cannot autohide. 

Well, that answers the question as to why I can't autohide it.
Can I remove it easily?
And then put it back when it's needed?

---

### Post by buzzingrobot on 2014-01-27
> **Damico said:**
> Well, that answers the question as to why I can't autohide it.
Can I remove it easily?
And then put it back when it's needed?

Nope.

Like the Launcher, it's a core piece of Unity. If you want a hide-able panel, you need to look at other interfaces for Ubuntu that do not use Unity.

---

### Post by Damico on 2014-01-27
> **buzzingrobot said:**
> Nope.

Like the Launcher, it's a core piece of Unity. If you want a hide-able panel, you need to look at other interfaces for Ubuntu that do not use Unity.

Thanks for letting me know. I'll just live with the panel then.  Too bad. But, such is life. I do appreciate the advice.
I guess that's why I couldn't find a way (because there isn't a way, short of changing the GUI).

Most of the time, I try to live with the GUI (there are bigger fish to fry normally); but, Unity is one of the hardest to live with (although no harder than trying to live with Windows 8, for example).

It's interesting, that most of these GUI "improvements" are all attempts to help people who can't find their own files, find their files.
But, what they end up doing is making it much harder for those who know where their files are, to just operate the desktop - simply because of the multiple levels of indirect.

Sigh.
[ / editorial comment ]

I'll mark this resolved (in so much as there is no answer to be had).

---

### Post by buzzingrobot on 2014-01-27
Unity seems to me to be a straightforward variation of the panel-and-dock approach.  That's not terribly innovative.  What is new, as it is in Gnome shell, is the positioning of search as a app launcher and app locator. 

Most people do not know where their files are, do not need to know (that's what computers are for, they will tell you) and they do not want to know.  From their point of view, it's the application's job to sort that out. iOS, apparently at the insistence of Steve Jobs, does just that rather well.  I don't think that represents a dumbing dowm, but a recognition of where the market is.  People are quite happy to use a particular capability or other if it is encapsulated in a straightforward application.  They are not at all happy with figuring out how to leverage a batch of tools to accomplish some new task. (That, of course, is why the traditional Unix approach has never been commercially successful.)

Files aka Nautilus is still there, as is Bash, for manipulating files.

---

### Post by SurfaceUnits on 2014-01-28
Ubuntu Gnome will work

---

### Post by vasa1 on 2014-01-28
> **Damico said:**
> I've easily enabled the auto-hide feature of the side launcher, so, now I just need to enable the auto-hide feature of the top menu.

But how?
What particular aspect of the top menu do you want to hide (given that the entire top menu cannot be auto-hidden)? If it's the **username** then look at this: ```

philipballew	if you want to show your name in the top pannel by the date:	18:35
philipballew	gsettings set com.canonical.indicator.session show-real-name-on-panel true	18:35
philipballew	and to reverse:	18:35
philipballew	gsettings set com.canonical.indicator.session show-real-name-on-panel false	18:35

```
Source: [http://irclogs.ubuntu.com/2014/01/25/%23ubuntu-classroom.html#t18:35](http://irclogs.ubuntu.com/2014/01/25/%23ubuntu-classroom.html#t18:35)

---

### Post by amoun on 2014-02-17
Well what a poor show. There's always a way but if you prefer fish then you will flounder :)
Still I'm on 8.4 so things are a bit simpler.

---

### Post by johf on 2014-10-19
One of the points of FOSS is that the users not only matter, they steer.  Nobody likes obstreperuous windows like a menu bar that won't go away, which is why as soon as they appear people start working on workarounds.  Humorous is the lengthy rational given to do something that users don't want.  Besides, the menus themselve fade until moused over so by the same stroke so should the menu bar itself.

---

### Post by Bucky Ball on 2014-10-20
@ johf: Welcome. Old thread. 13.10 is no longer supported. If you have general comments regarding FOSS, please post a new thread in a non-support area. This area is for support. Thanks and good luck.

*Thread closed.*

---

