---
title: "running armagetronad commands in terminal"
date: 2010-09-29
forum: Gaming &amp; Leisure
---

### Post by Affrikka on 2010-09-29
Hey everyone,

there is a lan party tomorrow so this kinda urgent :P

i have successfully set up a server with ubuntu and have armagetron, urban terror, and nexuiz all running and hosted on it.

how can i mess with armagetronad in-game settings form the terminal? since ubuntu server is all text, i can't really go into the game and play a round and mess with stuff. so how can I be in the terminal and change for example the wall length, or the game's server name (right now it just shows up as UNAMED SERVER)

sorry if this is a little vague, everybody is running really behind so.. thanks for all your help in advance!


Mathieux

---

### Post by dfreer on 2010-09-30
There is a config file somewhere where you can change these settings on the server itself, I believe it's /etc/default/armagetronad-dedicated.

Beyond that, once you connect to a running server from a client, you should be able to administrate that server by typing /admin in chat, then entering a password, and then issuing commands as if you were on the local server I believe. I haven't played with armagetron in years so all my info is based on a 5 minute google search.

---

### Post by Affrikka on 2010-09-30
> **dfreer said:**
> There is a config file somewhere where you can change these settings on the server itself, I believe it's /etc/default/armagetronad-dedicated.

Beyond that, once you connect to a running server from a client, you should be able to administrate that server by typing /admin in chat, then entering a password, and then issuing commands as if you were on the local server I believe. I haven't played with armagetron in years so all my info is based on a 5 minute google search.


thanks for the location of that configure file, i couldn't find it anywhere!!!

i think i got everything figured out now, thanks so much!

---

