---
title: "Stop and Start compiz command"
date: 2009-02-22
forum: General Help
---

### Post by mikedmor on 2009-02-22
Hi im working on making it so that when ever i start one of my games using Wine that all the compiz effects are turned off then when the game closes they automatically turn back on. I did a little research to find the commands to do this and found this:

```
sudo killall avant-window-navigator
killall compiz.real
xfwm4

#and to restart Engage
engage -b 70707099 -R 1 -Z 2 -d 0.32 -i 1 -I 1 -T 
```

My question is how do i make this code work when i start up a certain wine App and then when the app closes make the other command work to get my effects working again?

Also im sorry if i posted this in the wrong place. I do know that there is a wine forum but i couldnt decided if this really went with wine.

-Mike

---

