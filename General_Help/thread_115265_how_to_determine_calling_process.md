---
title: "how to determine calling process?"
date: 2006-01-10
forum: General Help
---

### Post by Whatsisname on 2006-01-10
Greetings. Awhile back I seem to have setup some sort of alert that calls mplayer to play a song. However, i have forgotten what program I set that up in, and want to investigate so I can turn it off. When it runs I have looked under ps and pstree to try and find the calling process, but those havent had the answer's I've looked for. Pstree outputs a tree when you run stuff under bash, but mplayer appears in there as a process directly under init which doesnt make sense. I've played around with parameters for both programs but no luck. Is there some other way to find out what is starting up mplayer? 

Thanks

---

### Post by schilcha on 2006-01-10
try ```
ps -eo pgid,pid,user,args --sort pgid
```
It will give you the process group id (pgid) in the first column. The find the process that has the same process id (pid) as the pgid of mplayer -- it's the process group leader.

btw, pid==1 means that the processes parent has gone -- init is taking care of the process (eg daemons do that)

---

### Post by Whatsisname on 2006-01-10
no dice, the output is basically identical to pstree. Many of the programs there have the same pgid as their pid.

---

### Post by schilcha on 2006-01-11
Sorry this didn't help you. 

I tried the procedure on my system with firefox-bin, which is directly connected to init in ps-tree output. However the "ps ..." statement gave 
> 
[...]
 8153  8153 rainer   gnome-panel --sm-config-prefix /gnome-panel-7QvrKx/ [...]
 8153  8266 rainer   /usr/lib/mozilla-firefox/firefox-bin -a firefox
[...]

From this I can see then firefox (pgid=8153) originated from gnome-panel (pid=8153) -- this is where I pushed the icon, so it seems reasonable.

Anyways, good luck!

---

