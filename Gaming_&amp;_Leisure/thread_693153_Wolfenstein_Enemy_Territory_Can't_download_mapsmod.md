---
title: "Wolfenstein Enemy Territory: Can't download maps/mods"
date: 2008-02-10
forum: Gaming &amp; Leisure
---

### Post by c/Kr3t on 2008-02-10
Whenever I try to connect to a server and download the maps or mods used there, it always kicks the game and pulls up lynx to download things for me. But when I choose to download something, it never seems to show up in my et directory and then I go to play the server and it does this all over again.  Can anyone help?

---

### Post by FrozenFox on 2008-02-10
I don't play the game, but i've installed and tried it out once. Essentially, take my advice with a grain of salt ;p. Anyway, it sounds to me like you have a permissions problem, and it's not downloading it perhaps because you installed the game with the wrong permissions (ie ran a script as root/sudo that shouldnt have been, or something). How did you install ET? Where is the ET folder with all the good stuff? Is there another one in /home/yourname/.enemy-territory or .et or something (notice the dot)? I imagine the ET folder(s) need to have their permissions changed from belonging solely to root to giving you write access. The simplest (but worst security wise i guess) way to do this is to sudo chmod 777 -R /path/to/ET/ on the game folder in the terminal/console/konsole under accessories.

---

### Post by c/Kr3t on 2008-02-10
it's in the /usr/local/games folder,  i think it's a permissions thing cuz i didn't put that command in till after i installed the game because i didn't read the whole page where i got it that i would need to enable permissions before installing. thank you for your help

---

### Post by frodon on 2008-02-11
My guess is that you miss rights on your .etwolf directory, run the following command and you should be ok :
```
sudo chown -R *your_username* ~/.etwolf/
```replace *your_username* by your username.

---

### Post by k1dicarus on 2008-02-18
I have this issue sometimes, too. What solved it for me was opening a terminal and typing sudo nautilus. Then navigate to the game's directory, double-click the icon, and open it that way.

---

### Post by reed026 on 2008-02-18
I had this problem last night and I ended up removing my .etwolf folder, restarting the game and then I could download maps.

---

### Post by frodon on 2008-02-19
> **k1dicarus said:**
> I have this issue sometimes, too. What solved it for me was opening a terminal and typing sudo nautilus. Then navigate to the game's directory, double-click the icon, and open it that way.Really bad idea, persons who read that do not do that, never run a game with root rights. It is not needed and make your system vulnerable to anything coming from the game you are running as root.

---

