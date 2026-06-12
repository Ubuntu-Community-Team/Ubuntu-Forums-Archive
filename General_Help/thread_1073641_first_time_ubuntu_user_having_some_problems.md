---
title: "first time ubuntu user having some problems"
date: 2009-02-18
forum: General Help
---

### Post by spedax on 2009-02-18
hi there,

I'm having some trouble.
I can't get my flash player installed,
I tried 
sudo apt-get install flashplugin-nonfree
[sudo] password for simon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
but it didn't work

also I got this notice if I wanted prohibitary video drivers ( I got a 9600GT Mobile ) and I said yes, but after giving in my password it flickers a prompt and then disappears, no drivers installed.

Hoped my first ubuntu try ( heard so many good things about it ) is gone go a little smoother then its going now :(

hope to hear more someone soon !

---

### Post by itang sanjana on 2009-02-18
flashplugin-nonfree is a multiverse repos.
Have you enabling multiverse repos first?
Check this out for the HowTo,
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
CMIIW

---

### Post by fooman on 2009-02-18
for the drivers,  have you tried going to system > administration > hardware drivers

see if there are video drivers listed there...if so try to enable them.

for flashplugin-nonfree,  i believe you will need to enable the multiverse/universe repositories....so go to system > administration > software sources.  on the "ubuntu software" tab...make sure the first 4 choices are checked off (main - universe - restricted - multiverse).

then run these 2 commands,  one at a time:

```
sudo apt-get update
``````
sudo apt-get install flashplugin-nonfree
```hope that helps.

edit...sorry,  i guess i was a little too late with that.

---

### Post by Therion on 2009-02-18
Try this instead:```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by wildman4god on 2009-02-18
you can also visit adobe's site and just download and install the deb.

---

### Post by spedax on 2009-02-19
thanks allot for the reply's, and yeah I didn't have multi/universal rep's on, and had to switch from belgium update servers to the main update servers. ( package manager wasen't working aswell)

Thanks again for all the info!

---

