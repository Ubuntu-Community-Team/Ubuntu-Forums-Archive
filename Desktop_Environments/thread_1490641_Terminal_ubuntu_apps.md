---
title: "Terminal ubuntu apps"
date: 2010-05-22
forum: Desktop Environments
---

### Post by dyltman on 2010-05-22
Hello, I'm thinking of experimenting abit with my desktop and I want to create a hacker looking desktop and thought I'd do this by having lots of terminal apps, I'd like to hear some of your suggestions on the following stuff.

1. What WM should I use (I'm thinking something in a style of awesome wm, that is a tiling one)
2. What terminal client should I use (the gnome terminal doesn't look very good with the menubar, I guess I could remove it but still any alternative would be cool
3. Some generic apps that are ran in the terminal (A nice media player, IM client (must have ICQ and MSN support), file manager, IRC client, mail client, generic gadgets like a clock for instance etc.)

---

### Post by Phrea on 2010-05-22
You might want to check [this](http://xwinman.org/) out.
Lots of WM's, lots of screenshots, a fun site.

EDIT: most screenshots do appear to be a little on the old side.

---

### Post by dyltman on 2010-05-22
> **Phrea said:**
> You might want to check [this](http://xwinman.org/) out.
Lots of WM's, lots of screenshots, a fun site.

EDIT: most screenshots do appear to be a little on the old side.

Yeah looks pretty outdated

---

### Post by mac9416 on 2010-05-22
Hi, dyltman,

Here are some of my thoughts.

Window manager:
[LIST]
[*][Openbox]("http://openbox.org/[") - not tiled, but very minimalist.
[*][Fluxbox]("http://fluxbox.org/") - similar to Openbox.
[/LIST]

Terminal:
[LIST]
[*][Terminator]("http://www.tenshu.net/terminator/") - just a simple terminal app.
[/LIST]
File manager:
[LIST]
[*][Midnight Commander]("http://www.midnight-commander.org/")
[/LIST]

Chat:
[LIST]
[*][irssi]("http://irssi.org/")
[*][naim]("http://naim.n.ml.org/about")
[/LIST]

Media player:
[LIST]
[*][MOC]("http://moc.daper.net/")
[/LIST]

Email:
[LIST]
[*][Mutt]("http://www.mutt.org/")
[/LIST]

Maybe some of those will be helpful.  :)

---

### Post by dyltman on 2010-05-22
alright thanks, lots of great apps. However I think I made up my mind and I'll go with awesome wm... yet I can't figure out how to exit an application in that thing :P

I forgot, any nice terminal based browsers?

---

### Post by SlidingHorn on 2010-05-22
> **dyltman said:**
> alright thanks, lots of great apps. However I think I made up my mind and I'll go with awesome wm... yet I can't figure out how to exit an application in that thing :P

I forgot, any nice terminal based browsers?

Take a look @ Lynx

```
sudo apt-get install lynx
```

Then: 

```
lynx google.com
```

---

### Post by dyltman on 2010-05-22
> **SlidingHorn said:**
> Take a look @ Lynx

```
sudo apt-get install lynx
```

Then: 

```
lynx google.com
```

awesome ty.

Anyone knows of a system monitor?

And also is there a black theme for Midnight commander?

---

### Post by mac9416 on 2010-05-22
I use lynx and like it a lot, but I've also heard of [Elinks]("http://elinks.or.cz/") as a terminal web browser. Should be worth checking out.

For the system monitor, you can't beat [htop]("http://htop.sourceforge.net/"). Even when I could use a GUI system monitor, I prefer htop.

---

### Post by m_duck on 2010-05-22
DWM and WMII are a couple of other window managers you could consider. As for a terminal, I tend to just use xterm, or occasionally urxvt.

In "other apps" I would add a +1 for MOC, and say that centerim is a pretty good IM client with a fair few protocols.

---

### Post by dyltman on 2010-05-22
I tried Elinks, however I found the terminal browsers to be messy without any images displaying.

---

### Post by tgalati4 on 2010-05-22
Got to have the moc for music and midnight commander (mc) for file browsing.

I also like rwho and ruptime for monitoring several machines at once.

aptitude for updating.

---

### Post by dyltman on 2010-05-22
> **tgalati4 said:**
> Got to have the moc for music and midnight commander (mc) for file browsing.

I also like rwho and ruptime for monitoring several machines at once.

aptitude for updating.

Yeah, I couldn't get moc to work when playing a mp3 file

---

### Post by Zemblan on 2010-05-22
MPD is a nice player for a terminal only desktop. It's a music server so you'll need a console based frontend for it, like mpc or ncmpc. Also htop is a decent system montitor, like top but prettier and with more functionality/customisability. Mutt is a decent email client, and as has been mentioned centerim is a good IM client.

---

### Post by Nythain on 2010-05-22
if you really want a console influenced setup, dont run X or a window manager :P

a fun list of console apps
Irssi - irc
mpd/ncmpc - music player daemon and player
htop - system monitor
centerim - multi instant messaging client
mc - midnight commander, ncurses based file manager
cmatrix - fun matrix scrolling stuff in a terminal
and many many more...

as for a terminal to use, im partial to rxvt-unicode and i use zsh as a shell

---

### Post by dyltman on 2010-05-23
> **Nythain said:**
> if you really want a console influenced setup, dont run X or a window manager :P

a fun list of console apps
Irssi - irc
mpd/ncmpc - music player daemon and player
htop - system monitor
centerim - multi instant messaging client
mc - midnight commander, ncurses based file manager
cmatrix - fun matrix scrolling stuff in a terminal
and many many more...

as for a terminal to use, im partial to rxvt-unicode and i use zsh as a shell

wow, I love the centerim and the cmatrix was also pretty cool. Still looking for a black theme to the mc as the default blue looks like a installation of windows XP

---

### Post by Nythain on 2010-05-23
> **dyltman said:**
> wow, I love the centerim and the cmatrix was also pretty cool. Still looking for a black theme to the mc as the default blue looks like a installation of windows XP
you can totally mod the colors now...

[http://plug-and-pray.blogspot.com/2009/09/editing-midnight-commanders-color.html](http://plug-and-pray.blogspot.com/2009/09/editing-midnight-commanders-color.html)

pretty freaking amazing...

---

