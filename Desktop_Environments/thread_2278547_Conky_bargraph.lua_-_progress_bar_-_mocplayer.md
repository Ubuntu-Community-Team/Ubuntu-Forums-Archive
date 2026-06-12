---
title: "Conky bargraph.lua - progress bar - mocplayer"
date: 2015-05-17
forum: Desktop Environments
---

### Post by trevo2 on 2015-05-17
Hello.

I have a question on how to "show" the progress of the current track being played by the moc player, in such a way as of bargraph_small2.lua 
                 [[IMG]http://wstaw.org/m/2015/05/13/zrzut_ekranu1_png_300x300_q85.jpg[/IMG]]("http://wstaw.org/w/3mVf/")

Here is an excerpt of my file bargraph_small2.lua:
```
{    --[ Graph for Memory ]--
            name="memperc",
            arg="mem",
            max=100,
            alarm=50,
            alarm_colour={0xFF0000,0.72},
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0x00FF00,0.55},
            mid_colour={{0.45,0xFFFF00,0.70}},
            x=8,y=396,
            blocks=70,
            space=1,
            height=4.6,width=13,
            angle=90,
            smooth=true
            },
```


Now resulting from the write file conky.conf 
                [[IMG]http://wstaw.org/m/2015/05/13/mocp_png_300x300_q85.jpg[/IMG]]("http://wstaw.org/w/3mVh/")

```
 ${voffset 11}${color 228B22}${execbar echo $((`mocp -Q %cs'*100/'%ts`))} 
```


How to use my bar configuration for this bargraph_small2.lua


Thanks!

---

### Post by CantankRus on 2015-05-18
The below link may be a better place to ask or find something you like.
A lot of the old users who know lua and conky have retreated to #!crunchbang
[http://crunchbang.org/forums/viewtopic.php?id=15356](http://crunchbang.org/forums/viewtopic.php?id=15356)

---

