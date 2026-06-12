---
title: "Runescape balck screen"
date: 2013-01-03
forum: Gaming &amp; Leisure
---

### Post by mrsjcmking on 2013-01-03
So I fixed the last issue, now runescape will load, I can login and then this happens

[IMG]http://i45.tinypic.com/2n8pvkh.png

Then when if I switch tabs it goes to this...

[IMG]http://i49.tinypic.com/33dwa5g.png

Any ideas?

---

### Post by HikariKnight on 2013-01-08
that is an odd one, first time i have seen it show up like that and then disappear if you switch tabs.
however black screens indicate that java is crashing.
you could do the usual fix of just making java use 512mb heap and 2mb stack size, sadly the website overrides your overrides though so you will have to use a wrapper or use the unofficial opensource native client port.

you can find info about both in the official wiki
[http://services.runescape.com/m=rswiki/en/Linux_Native_Clients#The_RuneScape_UNIX_Client_.28RSU_Client.29](http://services.runescape.com/m=rswiki/en/Linux_Native_Clients#The_RuneScape_UNIX_Client_.28RSU_Client.29)

there is a ppa for the client, however the wrapper needs to be manually installed because it acts as a forwarder for the java plugin (not a pretty solution but it works)

the easiest is to install the client thanks to the ppa

client+openjdk
```
sudo apt-add repository ppa:hikariknight/unix-runescape-client
sudo apt-get update
sudo apt-get install unix-runescape-client
```

just the client (if you already have java installed, this command is preferred by those that have oracle-java installed on the system)
```
sudo apt-add repository ppa:hikariknight/unix-runescape-client
sudo apt-get update
sudo apt-get install runescape
```

also for the future i suggest you post in linux thread in the runescape forums, it is much easier to get runescape support for linux from the players there, as they play the game themselves.
[http://services.runescape.com/m=forum/sl=0/forums.ws?25,26,99,61985129](http://services.runescape.com/m=forum/sl=0/forums.ws?25,26,99,61985129)

---

