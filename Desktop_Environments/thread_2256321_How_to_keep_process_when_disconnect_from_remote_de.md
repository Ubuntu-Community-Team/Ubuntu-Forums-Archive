---
title: "How to keep process when disconnect from remote desktop connection"
date: 2014-12-11
forum: Desktop Environments
---

### Post by hoang_minh2 on 2014-12-11
Hello everybody, i installed xfce4 + xrdp on ubuntu 14.04 32bit. When i remote with windows remote desktop connection, it's work fine. But when i disconnected and reconnected again, all processing was gone (e.g: firefox). How can i fix it?
I want to keep firefox working (i'm using it to download files) when disconnnect. Very sorry for my bad english.

---

### Post by lah7 on 2014-12-11
Welcome to the forums! I believe when you disconnect xrdp without logging out, it's still running in the background. When you re-connect, it instead connects to a fresh session.

The first answer here may help:
[http://askubuntu.com/questions/133343/how-do-i-set-up-xrdp-session-that-reuses-an-existing-session](http://askubuntu.com/questions/133343/how-do-i-set-up-xrdp-session-that-reuses-an-existing-session)

What you'll want to do is change the port that xrdp uses to connect to a session to a fixed one, such as 5901.

[COLOR=#b22222]**Edit: **See my next post on creating two entries, since you'll need port=-1 and port=5912.[/COLOR]

In a terminal:
```
sudo nano /etc/xrdp/xrdp.ini
```

And scroll down to **[xrdp1]** and change
```
port=-1
[B]to
[/B]port=5901
```

Port -1 means connect to any (the first one that's free)

Press** CTRL+X** then **Y** to save and restart xrdp for the changes to take effect:
```
sudo service xrdp restart
```

This might become a problem if you have other users connecting, since they'll connect to the same session.

---

### Post by hoang_minh2 on 2014-12-11
Hi, special thanks for your help. I do exactly follow your instruction, but i got this error.
[IMG]http://i.imgur.com/NmQ4lcl.jpg[/IMG]
What should i do? :(

---

### Post by lah7 on 2014-12-12
My bad! The port should have been 5912 (the first one xrdp sessions use). However, this only will connect when a session has already started.

What we can do is create another entry in **xrdp.ini** so that you have the two options: one to create a new session and another to connect to the first session.

In the **xrdp.ini**, you'll want the original **port=-1 **(which will create a new session) and** port=5912** as options.

Either add at the bottom, or cascade all the entries x*rdp2 to xrdp3, xrdp3 to xrdp4 etc* (if you want it near the top) so it looks like this:
```
[xrdp**1**]
name=[COLOR=#0000cd]New Connection[/COLOR]
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=**-1**

[xrdp**2**]
name=[COLOR=#0000cd]Existing Connection[/COLOR]
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=**5912**
[COLOR=#a9a9a9]
[xrdp3]
name=console
lib=libvnc.so
ip=127.0.0.1
port=5900
username=na
password=ask[/COLOR]
```

You can change the [COLOR=#0000cd]names[/COLOR] if desired.

Don't forget to restart xrdp again. When you connect for the first time, use the 'New Connection' option and login as normal. When you want to reconnect to the original (first) session you started, use the other option.

I just tested this and it works on my system. I hope it solves the problem.

---

### Post by hoang_minh2 on 2014-12-12
Awesome, it connnected sucessfully. thank you again :D

---

