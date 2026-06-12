---
title: "WIndows manager not working, no title bars, no window buttons"
date: 2010-12-12
forum: Desktop Environments
---

### Post by Browser_ice on 2010-12-12
Today upon booting my Xubuntu 9.04, I see that all new windows I open have their title bar missing and on top of my pannel menu.  If I try to run windows manager from the menu, nothing shows up on the screen. Therefore I think my windows manager is not running at all.

I have no graphic effects and dont want any.

I noticed that nothing shows up on the task bar (bottom bar) when I have anything opened up in the desktop. Can't minimize, can't click close button, ... This is very annoying

How do I fix this ?

I followed a thread to install Compiz and emerald just so I could get it to work but I do not like this option. I do not want any special effects. The more effects/options I have the more possible problems I may get.

By the way I also have this problem on my office Ubuntu 10.04. Both started having this problem recently. I suspect it is an update that was done that is causing this.

---

### Post by kevxh on 2011-01-05
Assuming metacity is your window manager use Alt+F2 and type in 
metacity --replace

This has happened to me a few times, I couldn't tell you what causes it but this command re-initializes metacity and all is good.

Kev

EDIT: Your signature says that you're using Xubuntu, so xfce is the windows manager, use
xfce4 --replace instead

---

### Post by TechWiz2100 on 2011-01-05
This is also sometimes caused by faulty graphics drivers.

I have Compiz installed and when my nVidia driver kicked the bucket, Compiz actively refused to load any window controls and even removing Compiz failed to work so I was forced to navigate my computer with half functioning keyboard shortcuts to open terminal and reinstall old drivers...

I know you said you don't use Compiz or other enhancements but my issue persisted in Gnome after I both turned off and removed Compiz

---

### Post by juanvi on 2013-02-22
Great! worked for me in xubuntu 12.04

> **kevxh said:**
> Assuming metacity is your window manager use Alt+F2 and type in 
metacity --replace

---

### Post by oldos2er on 2013-02-22
Old thread closed.

---

