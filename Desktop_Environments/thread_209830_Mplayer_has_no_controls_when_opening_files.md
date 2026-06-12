---
title: "Mplayer has no controls when opening files"
date: 2006-07-05
forum: Desktop Environments
---

### Post by elispiro on 2006-07-05
When I open a video file from limewire or frostwire, it opens in Mplayer, and instead of a skin, I get a terminal with status beside the play window. Is there a way to make the buttons show up, or even better, open up the files in Totem rather than mplayer?

---

### Post by Anduu on 2006-07-05
Mplayer does't have a gui...The gui version is called gmplayer.

Now I'm not quite sure how to change it but if you go to options in Limewire and you select Helper Apps yo will see the command for mplayer listed as:
```
xterm -e mplayer $URL$
```
This opens a terminal and launches mplayer from the command line.

Possibly you could try changing the entry to something like:
```

xterm -e gmplayer $URL$
```and see what happens.

---

### Post by elispiro on 2006-07-05
I'll try that, thanks!

---

### Post by Anduu on 2006-07-05
Doh...almost forgot make sure gmplayer is installed...duh :p

---

### Post by taurus on 2006-07-05
Actually, gmplayer is just a link to mplayer...

lrwxrwxrwx 1 root root 7 2006-06-04 15:33 /usr/bin/gmplayer -> mplayer

---

### Post by Anduu on 2006-07-05
[QUOTE=taurus]Actually, gmplayer is just a link to mplayer...

lrwxrwxrwx 1 root root 7 2006-06-04 15:33 /usr/bin/gmplayer -> mplayer[/QUOTE]

Well I guess it is true...you learn something new every day :wink:

---

