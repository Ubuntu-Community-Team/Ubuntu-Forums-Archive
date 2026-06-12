---
title: "I Broke Terminal"
date: 2006-06-09
forum: Desktop Environments
---

### Post by CarlosinFL on 2006-06-09
I was messing around in Terminal Preferences and selected the option to run a special command when I executed shell. I wrote the command in the empty box as "uptime" thinking that everytime I open terminal, it will run this command and keep the terminal window open...

Now when I run terminal, I can see it flash very fast and then vanish. :-s 

Does anyone know how I can disable the check in Terminal Preferences since I can't get to it any longer...

---

### Post by deadlycow21 on 2006-06-09
[QUOTE=Carlwill]I was messing around in Terminal Preferences and selected the option to run a special command when I executed shell. I wrote the command in the empty box as "uptime" thinking that everytime I open terminal, it will run this command and keep the terminal window open...

Now when I run terminal, I can see it flash very fast and then vanish. :-s 

Does anyone know how I can disable the check in Terminal Preferences since I can't get to it any longer...[/QUOTE]

try installing a different terminal. i know that there are 4 on suse.. try one of these.

---

### Post by CarlosinFL on 2006-06-09
[QUOTE=deadlycow21]try installing a different terminal. i know that there are 4 on suse.. try one of these.[/QUOTE]

I don't think just installing another shell window will do anything. I would like to resolve this terminal window issue.

---

### Post by BenTyreman on 2006-06-09
Alt+F2 to bring up the Run Application dialog. Type ```
gconf-editor
```
Go to apps -> gnome-terminal -> profiles -> Default. There's a key called "custom_command". Just delete whatever you put in there.

---

### Post by CarlosinFL on 2006-06-10
[QUOTE=BenTyreman]Alt+F2 to bring up the Run Application dialog. Type ```
gconf-editor
```
Go to apps -> gnome-terminal -> profiles -> Default. There's a key called "custom_command". Just delete whatever you put in there.[/QUOTE]

Just what I was looking for!!!

Thanks - You saved me from reinstalling.

---

### Post by Lunar_Lamp on 2006-06-14
To do what you wanted, I think you just need to add "uptime" to the end of your bashrc file (located ~/.bashrc).  You may need the full path of uptime, I can't remember - as I use a laptop, my uptime is not something I am too bothered about keeping track of ;)

---

### Post by msnel on 2007-12-13
> **BenTyreman said:**
> Alt+F2 to bring up the Run Application dialog. Type ```
gconf-editor
```
Go to apps -> gnome-terminal -> profiles -> Default. There's a key called "custom_command". Just delete whatever you put in there.

Phew that saved my day as well, I had the same problem but with a different command entered in the custom command box. So just out of curiosity, can anyone tell me what kind of commands this box is for then?

---

