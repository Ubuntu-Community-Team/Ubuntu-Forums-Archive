---
title: "URBAN Terror crashes PC"
date: 2014-11-23
forum: Gaming &amp; Leisure
---

### Post by Jonners59 on 2014-11-23
Hi, I am trying to set up and use urban terror for the kids.  I have a PC (called "server") I leave on as a storage device and then a number of PCs/Laptops that we use normally on our LAN.

Some years ago I set up Urban Terror on the "server", just running the game as a server, so that my kids could log on and play from the various pcs without having to go online.  Worked great, but then we stopped using it.  I have decided to do the same thing again, but....  When I set up the server as I select the last button I think it is "start server" the PC freezes and will only restart if I press the on/off button and reboot.

I also find on all the PCs and Laptops that when the Urban Terror app is launched, as soon as the kids start to try and play the laptop/PC freezes with a horrid noise and again will only respond by turning the device off via the on/off button.

I have downloaded the latest version from Urban Terror, and used the UPDATE version too.  Nothing works, and the kids are back to their PS3 and the fights.

Any ideas, please?

---

### Post by mastablasta on 2014-11-25
freezes? that's a bit radical.

first off how is the version of urban terror now installed?  is the same version on server as is on clients? does the server have a desktop or is this  a headless server. if headless, I would suggest connecting to it via SSH and then running top or htop to monitor for any strange activities (let's say memory leak or CPU/RAM, maybe also get some temperature readings). while you are at it check the log files for any clues on the crashes.

or you could try another alternative game like for example Enemy territory, you can add some bots with omnibot mod to make it more interesting. or if you have Wolfenstein files you can play coop Return to castle wolfenstein.
unreal tournament 2004 works well on older machines and it's interesting enough to play it, but you would need to buy it. they might have it on GOG. the bots in it are descent. I play with my bro usually against bots (don't like to go online much for games), I then added a small mod that logs various statistics from the game which I then share with my bro. so we can see who is best :-)

---

### Post by Jonners59 on 2014-11-26
Thank you MastaBlasta
Appreciate the time and effort of your reply.
1. Yes all the same and latest.  I should start over by deleting all incidences and then reinstalling.  Do you know if all that is included is in the extracted folder?  If so I guess I could just delete those and re download and install.
2. No, this is not a proper server, it is just a PC I run as a central storage.  So running latest Ubuntu, all up to date and xcfe.  It has 16Gib RAM and 4 core processor, both are running no more than >30%
So given it is not headless (unlike me. Also clueless :) ), how would I go about collecting this data?

3. I'll take a look at those other games.  Useful to know. :)

Jonners

---

### Post by mastablasta on 2014-11-26
oh that kind of PC to get frozen... it must take quite a bit of memory leak :-)

it's been a while since I tried Urban terror, I stopped soon after trying it as there weren't many servers available. and I couldn't get my brother to try it.

perhaps it might be really best to clean it all and do another reinstall. 

to monitor the state you can install htop then open terminal and just run htop. or you can just use default system monitor. I am not sure how it's called in Xubutnu since I use mostly Kubuntu. but if nothing else a simple light GUI system monitor is gkrelm: [http://gkrellm.srcbox.net/](http://gkrellm.srcbox.net/). it loks like it escaped from the 90's but it does it's job. should be in software center.

since this is run as server there might be some logs about the crashes in the game folder. you can also check system logs if you find anything interesting. there should be some log viewer in XFCE again I am not sure which one there is.

and to check the temperatures in a graphical way there is psensor: [http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/)
I think this one is in software center as well. I am not sure if additional packages are needed or not.

since it's a proper PC check that good GUI drivers are installed on it. bad drivers could cause freezing. 

another option I stress test. maybe it's a hardware issue and some kind of hardware test/demo running should show it.

finally I have another game suggestion for kids - World of Padman - has bot's, uses one of the quake engines so it runs on older PC, is free, Linux & Windows, you shoot at characters with water balloons, paintball guns etc. maps are made as if the player is very small. so for example there is a kitchen map and you would run around the fridge, cupboards, in the oven etc. when you "kill" the opponent drops a paint bottle. you have to collect them and spray them on your teams wall. the team that sprays the fastest wins etc. it's all designed in a fun way. the creators planned a single player campaign but got stuck on multiplayer only. well at least the bots are descent.

---

### Post by Jonners59 on 2014-11-26
Yes, that type, actually it is 8 core, not 4 so plenty of ooooph, hence why I use it.  I just want the game(s) running in the background for them to log in to on the other laptops and pcs, unless they have some m8s around and want to kill each other as is often the case and we need it for one of the boys to play on.  It does also host a VM running our telephone system, but again I have accounted for that.

I will take a look at those tools, the problem I find is if I run UT I loose the mouse and can't get it back so have to reboot using the on/off button!  Not great.

Thanks for the other games.  Will try those.

Actually, whilst typing this I had installed the latest version and tried to run it and again it has stopped and I can't get my mouse back to shut it down or anything else !!!!!   GGGgggrrrr

Jonners

---

### Post by mastablasta on 2014-11-27
what kind of mouse is it?

otherwise if keyboard works atl+t to get terminal (or crtl+alt+F1 through F6 will get you into other consoles) then just 

```
sudo shutdown -h now
``` to turn it off 

or
```
sudo reboot
```

to reboot it.

perhaps only the mouse is freezing?

but hard to say what is wrong without logs or at least some error message.

---

### Post by Jonners59 on 2014-12-04
Shut down is not what I want to do when it locks up, buty getting out of the app so I can just shut down UT.

How can I create a log/info?

As soon as I select "Start" after the config is set up then nothing works.  It just freezes.

---

### Post by mastablasta on 2014-12-10
> **Jonners59 said:**
> 
How can I create a log/info?


This information should be available on urban terror site. it should be some developer mode or something.

anyway I am lately experiencing something similar with 2 games Enemy territory and Doom with Doomsday engine (or whatever is called now)  with OpenGL. Complete freeze& crash. but I have clients doing this. I wonder what could cause such a crash on server PC. I am suspecting certain (sound or GPU) driver cause the crash in my case but I haven't pinpointed it. especially since a few games like supertuxkart, minetest, minecraft work nicely.

one thing that could be interesting to try is maybe to run the server from another TTY. so switch to let's say first TTY - e.g. ctrl+alt+f1, login with your user and run the server. oh and ctrl+alt+f7 will get you back to desktop. but leave it running only in terminal console for a while. it's a crazy idea, but it might be crazy enough to work. :P

---

### Post by Jonners59 on 2015-01-15
> **mastablasta said:**
> This information should be available on urban terror site. it should be some developer mode or something.

anyway I am lately experiencing something similar with 2 games Enemy territory and Doom with Doomsday engine (or whatever is called now)  with OpenGL. Complete freeze& crash. but I have clients doing this. I wonder what could cause such a crash on server PC. I am suspecting certain (sound or GPU) driver cause the crash in my case but I haven't pinpointed it. especially since a few games like supertuxkart, minetest, minecraft work nicely.

one thing that could be interesting to try is maybe to run the server from another TTY. so switch to let's say first TTY - e.g. ctrl+alt+f1, login with your user and run the server. oh and ctrl+alt+f7 will get you back to desktop. but leave it running only in terminal console for a while. it's a crazy idea, but it might be crazy enough to work. :P

Sorry I did not get back, things over took me a bit...  Had major issues as you may have seen form a couple of threads I ran.

I have just started a new thread here and on the UT forum - same question.  Basically asking how to set up a home use UT, though I still have to find a way round this screen freeze issue and I would also like to know how to pop in and out of the ap back to the desktop without shutting it down every time.

---

