---
title: "GPU temperature on Superkaramba"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Eazy© on 2006-08-25
Hi all!

Im trying to ad GPU temp on my Superkaramba theme using [this]("http://www.kde-look.org/content/show.php?content=16119")

I have experimented a bit but i cant make it to print only the temp. I get a "can" in my theme that I cant remove. I use this to print to my theme:
```
nvidia-settings -q gpucoretemp | grep ': '| cut -d ' ' -f 6 # | awk '{print $4 0}'
```

Tried "man cut" but I dont understand it. Anyone that can help me I would be much gratefull :)

[Here]("http://web.telia.com/~u00175529/desk.png") is my desktop if somone is interested :)

---

### Post by Eazy© on 2006-08-26
Sorted it out by myselfe. I added [COLOR="Red"]LINE=1[/COLOR] like this:
> text x=175 y=82 sensor=program program="nvidia-settings -q gpucoretemp | grep ': '| cut -d ' ' -f 6 #| awk '{print $4 0}'" interval=10000  [COLOR="Red"]LINE=1[/COLOR] align=right color=255,255,255 FONTSIZE=10 FONT="Verdana"

---

