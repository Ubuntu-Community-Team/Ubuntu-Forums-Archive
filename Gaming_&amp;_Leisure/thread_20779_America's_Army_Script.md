---
title: "America's Army Script"
date: 2005-03-18
forum: Gaming &amp; Leisure
---

### Post by Bicet on 2005-03-18
I would like to make a little script that execute this simple commands

killall esd

and after that

$home/armyops/.armyops

I'm just a little newb, anyone can help me?

Thnx in advance

---

### Post by DJ_Max on 2005-03-18
```
$home/armyops/.armyops
``` 
Is this suppose to start the game?

---

### Post by Bicet on 2005-03-19
[QUOTE=DJ_Max]```
$home/armyops/.armyops
``` 
Is this suppose to start the game?[/QUOTE]
 Yes this will start the game

---

### Post by DJ_Max on 2005-03-19
Ok, well, then, this should work. And I won't charge you. ;) 
```

#!/bin/sh

#Kill ESD sound manager
echo "Killing ESD...."
killall esd
#Start AA
echo "Start Americas Army............"
${HOME}/armyops/.armyops


```

Copy and paste this as aa.sh, and place it somewhere in your home directory.

Then via the command line, do
sh aa.sh

---

### Post by Bicet on 2005-03-19
Thnx a lot ;)

---

### Post by DJ_Max on 2005-03-19
[QUOTE=Bicet]Thnx a lot ;)[/QUOTE]
 Does it work? I'm pretty sure it would, just basic Shell stuff.

---

### Post by Bicet on 2005-03-19
Yeah It's working like a charm ;)

---

### Post by DJ_Max on 2005-03-19
[QUOTE=Bicet]Yeah It's working like a charm ;)[/QUOTE]
 Ok, good, need anything else let me know 8)
I can also write one in Python that'll log the times you started, and stuff. But guess thats an overkill. :-P

---

### Post by Bicet on 2005-03-21
I don't know why, but after the first training I'm not able to access the second :(

---

### Post by arrizaba on 2005-03-22
Have you register in America's Army page?

[HTML]http://www.americasarmy.com/[/HTML]

If you don't register, then you cannot advance in training. So, eventually, you cannot play the game.
By the way, I would make a symbolic link for the aa.sh script so you can use it anywhere. I do not recommend you to have stuff hanging around in your home directory. Just place the script in your favourite /bin directory or make a symbolic link.

---

### Post by Bicet on 2005-03-23
[QUOTE=arrizaba]Have you register in America's Army page?

[HTML]http://www.americasarmy.com/[/HTML]

If you don't register, then you cannot advance in training. So, eventually, you cannot play the game.
By the way, I would make a symbolic link for the aa.sh script so you can use it anywhere. I do not recommend you to have stuff hanging around in your home directory. Just place the script in your favourite /bin directory or make a symbolic link.[/QUOTE]
 I've solved my isuue, it was a firewall problem ;)

---

### Post by arrizaba on 2005-03-23
Well, ahum, yes. If you have a firewall then you always get troubles....  :grin: 
Btw, cool avatar!

---

