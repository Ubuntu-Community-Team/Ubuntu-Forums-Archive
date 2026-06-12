---
title: "Weird command-line on bootup??"
date: 2007-12-09
forum: Desktop Environments
---

### Post by lhamil64 on 2007-12-09
I decided to install Ubuntu (latest version) to a computer that only has 128 mb of ram because XP was really really slow on it. After the install, now all i am getting is a commandline on bootup. Is the GUI still in there and i just need to type a command to get into it? or do i have to install it somewhere..

please help..

thanks,
lhamil64

---

### Post by mnemosyne on 2007-12-09
When you boot the computer does it ask you for your username? If it does log in and type "startx" (without quotes). BTW, I would recommend using Xubuntu instead of Ubuntu on a machine with 128MB of RAM (Ubuntu may be slow). Good luck :).

---

### Post by lhamil64 on 2007-12-09
ok ill try startx. If it's too slow i may use xubuntu.
This computer i won't use much so its not too big of a deal

EDIT:
i typed in startx and it said that the command was not found..
I also remember somewhere that said you could type in something like apt-get desktop on a server and it would give you a desktop. i tried that command and it didn't work either.

---

### Post by mcduck on 2007-12-09
So did you install with the Server disk? It doesn't have a graphical interface by default.

The command to install a desktop is 'sudo apt-get install xubuntu-desktop', and you need to have a working internet connection to do that.

---

### Post by lhamil64 on 2007-12-09
I did not install the server, i was just saying that somewhere someone said that and i thought it might work. One thing that might be helpful, is during install when it got to select software to install or something it got to 6% and froze there for a long time. Then it finally said that it failed and brought me to the step selector.
Also, in the list it said first Install GRUB and then Install LILO. I thought that they were both different steps so i ran both. I think the LILO one screwed something up because when i turned it on it said something about it starting, and then booted into text mode. Also, the wireless internet isn't working right (the adapter i mean) or something because it said it couldn't find the access point (this also happened on windows) and i'm not sure if it's working now or not. I entered my network name and key and it didn't really say much so im not sure.

---

### Post by mnemosyne on 2007-12-09
Try installing using the [Xubuntu alternate cd]("http://torrent.ubuntu.com/xubuntu/releases/gutsy/release/alternate/"). You want the third file down.

---

### Post by lhamil64 on 2007-12-09
ok. good thing i used a rewriteable CD, i can just erase it and put xubuntu on it.

---

