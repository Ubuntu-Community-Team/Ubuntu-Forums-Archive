---
title: "where can i find... ?"
date: 2010-07-12
forum: Desktop Environments
---

### Post by gobbledigook on 2010-07-12
in 10.04 where can i find the text file which holds the details for start-up applications? 

i run xbmc to my tv and its a pain in the *** to minimise it cause the box is under the stairs!! (me under the stairs typing... the tv still in the lounge ;) )

so i try to admin by ssh

---

### Post by gobbledigook on 2010-07-14
*bump*

---

### Post by nothingspecial on 2010-07-14
You`ll find it at ~/.config/autostart if you are running gnome, but if that`s the case it is probably easier to forward X during your ssh session and type 

```
gnome-session-properties
```

That will bring up the System > preferences > startup applications gui.

---

### Post by gobbledigook on 2010-07-14
> **nothingspecial said:**
> You`ll find it at ~/.config/autostart

didnt' work for me... the file wasn't there...

```
gnome-session-properties
```

using x forwarding over ssh worked a charm :) i can 't thankyou enough!

plus for future ref, to forward x over ssh you simply do:

```
$ssh user@host -X
```

---

### Post by nothingspecial on 2010-07-14
Let me expand on that tip a little. If you go System > Preferences > Main menu and select an item then click properties, it will tell you the command used to launch it.

So you want to set printing up on your box under the stairs over ssh. If you have a look in the main menu you`ll see its system-config-printer

Then you don`t have to start messing about with cups config files

You can even type gnome-panel and go click crazy

---

