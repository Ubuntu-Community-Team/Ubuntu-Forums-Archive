---
title: "Problem with WoW + Ubuntu 7.04"
date: 2007-07-19
forum: Gaming &amp; Leisure
---

### Post by lawlbbq on 2007-07-19
On load wow crashes, and the app closes. The computer functions perfectly fine after that. Does anyone have a solution? I already added the lines to my Xorg.Conf file, so thats out of question.

---

### Post by ubuntu.daemon on 2007-07-19
there is a great place on winehq.com  which lots of linux users use for WoW....
[http://appdb.winehq.org/appview.php?iVersionId=8136]("http://appdb.winehq.org/appview.php?iVersionId=8136")

---

### Post by corevette on 2007-07-19
Try running WoW on the terminal and typing
```
cd ~
cd .wine/
cd drive_c/
cd Program\ Files/
cd World\ of\ Warcraft/
wine wow.exe
```
The location above is only if you installed it in the default directory

Paste the output

---

### Post by ubuntu.daemon on 2007-07-19
lol you're half right, if he does that of course hes gonna get screwed.

you need to do either:

```
user@home:~/.wine/drive_c/Program Files/World of Warcraft$ wine wow.exe -opengl
```

or 

```
user@home:~/.wine/drive_c/Program Files/World of Warcraft$ wine wow.exe -d3d
```

Oh for WoW also to work you need to install MOZILLA, not FIREFOX, under WINE!!!

SO go download the Windows version from the site....

but if you go to that **winehq** site they will provide you with more answers and support than people here on these forums will....

:popcorn:

---

