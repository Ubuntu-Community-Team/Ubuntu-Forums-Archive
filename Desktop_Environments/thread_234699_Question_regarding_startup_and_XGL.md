---
title: "Question regarding startup and XGL"
date: 2006-08-11
forum: Desktop Environments
---

### Post by ice_gamer on 2006-08-11
I have been using XGL on Dapper 6.06 for quite a few months now and have loved it.  Unfortunately, I have to enable it with what I feel is sort of a "hack" everytime I start up.  Here is the code that I put into the gnome terminal in order to get XGL working:

```
LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 compiz --replace gconf && gnome-window-decorator
```

This code that I put in will enable all the XGL effects.

Is there a way I can have it where this automatically executes without me having to do this everytime I startup my computer?  I am adept at this stuff, yet, if you have any advice, please speak as plainly as possible so I can understand.  Thanks in advance.

---

### Post by kop316 on 2006-08-11
Well in this post

[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

he makes a bash command called thefuture

First this command:
Code:

sudo gedit /usr/bin/thefuture


And empty file should appear. Fill it with this:
Code:

#!/bin/bash gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &


Now save the file. Now use this command:
Code:

sudo chmod 755 /usr/bin/thefuture



Then wut i did is go to session and go to startup programs, clicked add and typed in thrfuture

---

### Post by kop316 on 2006-08-11
#!/bin/bash
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

after #!/bin/bash should be a return

---

