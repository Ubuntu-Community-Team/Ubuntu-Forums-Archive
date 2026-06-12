---
title: "Multiple X servers"
date: 2005-04-25
forum: Gaming &amp; Leisure
---

### Post by zwaardmeester on 2005-04-25
Hi, I have a little problem setting up an extra X-server. 

The reason I want an extra server is that you can switch from and to your game without leaving it (~ alt/tab in windows). This comes especially in handy for games without a windowed-mode option (like Diablo2). 

This is what I did:

started a new X server
```
sudo X :1.0
``` 
gave myself access to it in xauth
```
xauth add :1.0 MIT-MAGIC-COOKIE-1  68d682a4f137b4f46.....
```
added "Display" = ":1.0" to my Cedega (=wineX) config & started Diablo II.exe into the new X-server. But then it goes wrong. Wine keeps running (according to my System Monitor) , but nothing happens in my new screen. 

Other applications work well though, like the xterm.
```

leo@zwaardmeester:~$ export DISPLAY=':1.0'
leo@zwaardmeester:~$ xterm &

``` 

Anyone any idea what I'm doing wrong? 

ps. I have used [this](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=43) guide

---

### Post by Burgundavia on 2005-04-25
Multiple X servers on the same hardware is very untested. Basically sometimes it works and sometimes it doesn't.

Corey

---

### Post by nad on 2005-04-25
Look in your system logs for an error message regarding connection to display 1.

Diablo may not have authorization. The simple way to overcome this, as you do not know what services need to connect to your second display, is to remove all authorization. From the xterm on display 1 issue the command: xhost +

You appear to be on track. Good work.

---

