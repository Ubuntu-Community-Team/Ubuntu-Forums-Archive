---
title: "Uninstalling a app with uninstall shell script"
date: 2006-08-15
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-08-15
Im so nooby how do you do this ive been trying to figure this out :S

---

### Post by BitTorrentBuddha on 2006-08-15
First make the uninstall script executable and then run it. (replace /path/to/file.sh with the path to the shell script.)```
sudo chmod +x /path/to/file.sh
sudo /path/to/file.sh
```

---

### Post by WalmartSniperLX on 2006-08-15
> **BitTorrentBuddha said:**
> First make the uninstall script executable and then run it. (replace /path/to/file.sh with the path to the shell script.)```
sudo chmod +x /path/to/file.sh
sudo /path/to/file.sh
```

Thanks! ur a hero :p :D

---

### Post by WalmartSniperLX on 2006-08-15
> **WalmartSniperLX said:**
> Thanks! ur a hero :p :D

I did this command but it seems to not be making it executable :confused:

EDIT: woops didnt mean to quote myself ](*,) ](*,)

---

### Post by BitTorrentBuddha on 2006-08-15
chmod +x didn't make it executable? Was there any output when you finished running the command? If so can you post it in here. Alternatively you can try running it as:```
sudo sh /path/to/file.sh
```

---

### Post by WalmartSniperLX on 2006-08-15
> **BitTorrentBuddha said:**
> chmod +x didn't make it executable? Was there any output when you finished running the command? If so can you post it in here. Alternatively you can try running it as:```
sudo sh /path/to/file.sh
```


patrick@patrick-desktop:/usr/local/games/armyops$ sudo sh /usr/local/games/armyops/uninstall
Could not find a usable uninstall program. Aborting.
patrick@patrick-desktop:/usr/local/games/armyops$




Heres for that last command. Im gonna try chmod again

BTW for the extension do i use .sh or do i replace that?

---

### Post by BitTorrentBuddha on 2006-08-15
It depends what the script is called, if it's uninstall.sh type that, if it's just uninstall just type unintstall.

---

### Post by WalmartSniperLX on 2006-08-15
> **BitTorrentBuddha said:**
> It depends what the script is called, could you post the output of: ```
ls /usr/local/games/armyops
```

patrick@patrick-desktop:~$ ls /usr/local/games/armyops
Animations           Briefings  Maps          Sounds        uninstall
armyops              Demos      Movies        StaticMeshes
ArmyOps250_EULA.txt  Help       Music         System
ArmyOps.xpm          KarmaData  README.linux  Textures
patrick@patrick-desktop:~$

---

### Post by BitTorrentBuddha on 2006-08-15
When you ran ls, was 'uninstall' green? If so you should just be able to type: ```
sudo /usr/local/games/armyops/uninstall
```

---

### Post by WalmartSniperLX on 2006-08-15
> **BitTorrentBuddha said:**
> When you ran ls, was 'uninstall' green? If so you should just be able to type: ```
sudo /usr/local/games/armyops/uninstall
```

no it wasnt even highlighted ](*,)

EDIT: although armyops is green, if that accounts for anything ;)

---

### Post by BitTorrentBuddha on 2006-08-15
I'm stumped :-k , one last thing to try would be to do ```
sudo nautilus /usr/local/games/armyops
``` and then right click uninstall and choose 'Properties.' From there select the permissions tab and make sure that it's executable by the owner.

---

### Post by WalmartSniperLX on 2006-08-15
> **BitTorrentBuddha said:**
> I'm stumped :-k , one last thing to try would be to do ```
sudo nautilus /usr/local/games/armyops
``` and then right click uninstall and choose 'Properties.' From there select the permissions tab and make sure that it's executable by the owner.

Ok then thanks for the help I really appreciate it :-D  and thanks for posting in general :D Ill give it a try

---

