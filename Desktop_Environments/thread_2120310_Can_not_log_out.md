---
title: "Can not log out"
date: 2013-02-26
forum: Desktop Environments
---

### Post by meraj21 on 2013-02-26
I am using different desktop environment. When I log out from one to log in another, I see the new name so I log into that. But now I can not remember the name.
Now I can not log out from the environment. And can not do other things. Mouse works, but with right click nothing appears. 

Present state of my desktop:
[http://img194.imageshack.us/img194/3670/img7234b.jpg]("http://www.google.com/url?q=http%3A%2F%2Fimg194.imageshack.us%2Fimg194%2F3670%2Fimg7234b.jpg&sa=D&sntz=1&usg=AFQjCNH6ogV8JB_nATlAh7sErKVL70rcZQ")

Only top date bar shows. When I use arrow key in time of restarting those writings show.
Main thing is, I try to install tor browser. And after install I can't run it. So I try to change desktop environment.[COLOR=#888888]
[/COLOR]

---

### Post by unheeding on 2013-02-26
Looks like a problem with your X server.

Go to a virtual terminal (ctrl+alt+F1), log in, and then type:

$ ps aux | grep lightdm

You should see a few processes:

```
root      1683  0.0  0.8 270708 31228 ?        SLsl 14:11   0:00 lightdm
root      1717  6.3  5.1 506788 188216 tty7    Ss+  14:11  12:03 /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
root      3199  0.0  0.1 177188  3976 ?        Sl   14:11   0:00 lightdm --session-child 12 21
user     25868  0.0  0.0  13588   916 pts/2    S+   17:19   0:00 grep lightdm

```

See the one that starts with /usr/bin/X ?  That's the one we are going to kill.

$ sudo kill 1717  #replace 1717 with the number next to your /usr/bin/X process


It should take you back to the login screen, where you can select a different desktop environment/window manager.

---

### Post by meraj21 on 2013-02-26
Thank brother, it's works. Now I am in relief.

Again thank you very much.

---

