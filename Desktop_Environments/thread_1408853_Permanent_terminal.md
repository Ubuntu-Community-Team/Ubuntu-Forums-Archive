---
title: "Permanent terminal"
date: 2010-02-16
forum: Desktop Environments
---

### Post by Genitruc on 2010-02-16
Hi everyone,

                 I'd like to have a startup application that opens a terminal with the option that makes it visible on every workspace. Moreover, it could be nice to have a new terminal that comes up every time I close it. I know how to have an open terminal at startup but I don't know how to have these specific options.

P.S. It's the first time I use this forum, sorry if it's not the right place to post this question.

Genitruc

---

### Post by nilarimogard on 2010-02-17
You should try guake (sudo apt-get install guake) on Gnome or yakuake on KDE. That's a terminal that will come down each time you press the F12 key - Quake style. Another way would be to [embed a terminal into the desktop]("http://www.webupd8.org/2009/05/ubuntu-embed-terminal-into-you-desktop.html")

---

### Post by nothingspecial on 2010-02-17
> **Genitruc said:**
> Hi everyone,

                 I'd like to have a startup application that opens a terminal with the option that makes it visible on every workspace. Moreover, it could be nice to have a new terminal that comes up every time I close it. I know how to have an open terminal at startup but I don't know how to have these specific options.

P.S. It's the first time I use this forum, sorry if it's not the right place to post this question.

Genitruc

If you are running compiz 

```
sudo apt-get install compizconfig-settings-manager
```

if you haven`t already.

Make sure you have a terminal open.

Go system > preferences > compizconfig settings manager

Find window rules near the bottom and enable it.

Click on it and click the + on the right hand side of the line starting with sticky. Then click on the terminal and accept the rule.

Now any time you open a terminal it will be on all desktops.

Have a look at screen with byobu which will let you open and close and detach and reattach terminals within the same terminal

```
sudo apt-get install byobu
```

```
man byobu
```

Scroll down to the keybindings to see how to do it.

---

### Post by Genitruc on 2010-02-17
> **nothingspecial said:**
> If you are running compiz 

```
sudo apt-get install compizconfig-settings-manager
```

if you haven`t already.

Make sure you have a terminal open.

Go system > preferences > compizconfig settings manager

Find window rules near the bottom and enable it.

Click on it and click the + on the right hand side of the line starting with sticky. Then click on the terminal and accept the rule.

Now any time you open a terminal it will be on all desktops.

Have a look at screen with byobu which will let you open and close and detach and reattach terminals within the same terminal

```
sudo apt-get install byobu
```

```
man byobu
```

Scroll down to the keybindings to see how to do it.
Thanks everyone for those quick answers, it gives me some options. I used compiz before for desktop effects but I found it a bit unstable so I removed it. I have just tried guake and it seems a good alternative, the only detail is that guake minimizes each time I open a new window. I'd like to have the terminal as backgroud....(I think compiz does it). So far, with guake as a startup application should be the best solution.

Thanks again
Genitruc

---

