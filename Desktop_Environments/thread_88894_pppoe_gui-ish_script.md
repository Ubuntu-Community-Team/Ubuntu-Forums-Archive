---
title: "pppoe gui-ish script"
date: 2005-11-11
forum: Desktop Environments
---

### Post by trash on 2005-11-11
I don't know why a gui doesn't exist yet but anyway I'd like to create a small script that will take care of this. What i'd like it to do when launched is:

1. Check if an /etc/ppp/peers/dsl-provider file exists if yes #2 and if no launch pppoeconf in terminal to configure

2. if /etc/ppp/peers/dsl-provider exists launcher will execute sudo killall pppd(because one never knows how many pppd's are running) and then sudo pon dsl-provider.. basically it just restarts it

thats pretty much about it, i don't really see an immediate need for a poff but if it can be done that would be cool, either seperate script or same script with a popup start/stop dsl connection, but that could get a bit complicated lol.

At the moment I don't know where to start yet so i figured i'd post just incase some eager script writer can whip one off :)

cheers

---

