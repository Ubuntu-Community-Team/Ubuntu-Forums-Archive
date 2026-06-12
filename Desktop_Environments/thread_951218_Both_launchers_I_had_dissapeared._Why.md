---
title: "Both launchers I had dissapeared. Why?"
date: 2008-10-17
forum: Desktop Environments
---

### Post by MyCapitol on 2008-10-17
So umm, today I logged on and thought, 'hey, I want a new bootsplash' so i downloaded a new bootsplash and i guess installed it w/  startup manager. 

But when I rebooted it did not show up. So i thought i might've forgot to select the bootsplash when i installed it. But then when I logged on both launchers I had (bottom and top) did not come up.

I tried right clicking to create a new one but it never actually comes up.

Whats wrong?

The only thing I can do Is start rythmbox and  firefox since I have them on a keyboard shortcut but thats it.

Also before I reboot I uninstalled Pidgin, Evolution, and Frostwire and Nexuiz.

Also if it helps when I tried recovery mode and tried to fix broken packages..umm... it like failed to connect to repositories or something... but it failed.

How can I fix this?

---

### Post by gali98 on 2008-10-17
wow,,,
My guess is you uninstalled a lot more than you thought.
Pidgeon and Evolution are ubuntu default apps, and by uninstalling them, you may have unistalled a majority of GNOME.
My suggestion is to plug the computer into a ethernet connection before starting the copmuter.
Then power it on and go into the recovery mode.
Use the command 
sudo apt-get install ubuntu-desktop

and let it install everything. After that reboot and see if that fixes anything.
Kory

---

### Post by MyCapitol on 2008-10-18
> **gali98 said:**
> wow,,,
My guess is you uninstalled a lot more than you thought.
Pidgeon and Evolution are ubuntu default apps, and by uninstalling them, you may have unistalled a majority of GNOME.
My suggestion is to plug the computer into a ethernet connection before starting the copmuter.
Then power it on and go into the recovery mode.
Use the command 
sudo apt-get install ubuntu-desktop

and let it install everything. After that reboot and see if that fixes anything.
Kory

It says its unable to fetch repositories.

so umm.. doesnt fix it...

Do I just install new Ubuntu again?...

...the new beta version...

---

### Post by gali98 on 2008-10-18
Well If you haven't put a whole lot into this install, that might be a good idea.

But did you plug into a ethernet connection?
Try running the command
sudo apt-get update
first, then run the command I gave you in my other post....
Kory

---

### Post by MyCapitol on 2008-10-27
> **gali98 said:**
> Well If you haven't put a whole lot into this install, that might be a good idea.

But did you plug into a ethernet connection?
Try running the command
sudo apt-get update
first, then run the command I gave you in my other post....
Kory

umm... i installed it....
had a backup...thats good

---

