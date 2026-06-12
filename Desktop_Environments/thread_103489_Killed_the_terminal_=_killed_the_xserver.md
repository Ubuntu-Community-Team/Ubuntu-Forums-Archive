---
title: "Killed the terminal = killed the xserver?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Nils-Johan on 2005-12-14
Hi,
After using Breezy for awile i ran into trouble....
While virus scanning i accedently killed the terminal with the neat result that all my gnomepanels vanished.
Naive as i am i hit ctrl-alt-backspace to restart the xserver. Now i cant get back into my desktop. 
And i cant use any commands like sudo, locate etc just says "command not found".

---

### Post by daller on 2005-12-14
Just a question... Why where you virus-scanning?

From a terminal, what does "startx" give you?

Have you tried running "dpkg-reconfigure xserver-xorg"

---

### Post by Nils-Johan on 2005-12-14
I got a spywere/virus/trojan alert from google. As i (very rare) use IE under crossover i got paranoid. got two worms in my fake windows...

during start up everything turns green all the way until xserver starts up, it starts up but just for a couple of seconds then i get thrown out to the prompt. 
When i type anything that needs the sudo command i get "command not found"
i tried sudo dpkg-reconfigure xserver, ubuntu-desktop and gnome-panel and all a get is "command not found"
when i run "startx" i get "command not found"
i am a bit confused.

---

### Post by daller on 2005-12-14
It sounds bad!

Having any important data? - Use a LiveCD to backup!

Having no important data? - Use an InstallCD!

---

### Post by Nils-Johan on 2005-12-14
arrghhh!
Then i got another problem....
Right now i got knoppix 3.7 up an running but i cant mount the /home partition, but i can under ubuntu. The system i set up with LVM, can that be the couse to knoppix failure to mount the partition?

Can the M$ worms infect my system?

---

### Post by daller on 2005-12-14
[QUOTE=Nils-Johan]arrghhh!
Then i got another problem....
Right now i got knoppix 3.7 up an running but i cant mount the /home partition, but i can under ubuntu. The system i set up with LVM, can that be the couse to knoppix failure to mount the partition?

Can the M$ worms infect my system?[/QUOTE]

The Worms should have no effect!

Have you tried the Ubuntu LiveCD?

---

### Post by Nils-Johan on 2005-12-14
Do you know if there is some way to switch bashes to be able to use commands like ftp or something to send files over the network without the need use a live-cd?
But if that don't exist the i guess i'll try the ubuntu live-cd instead of knoppix...

---

### Post by daller on 2005-12-14
If you can't run any commands, that'll be quite hard!

Are you having any problems running a LiveCD?

---

### Post by Nils-Johan on 2005-12-14
right now i have problems with getting a live-cd as the ubuntu image is to large for the ramdisk/knoppix and as i can't mount my lvm partition under knoppix i can't do anyting to get more space....

Commands i can run is thoose that don't need root priv.

---

### Post by vruum on 2005-12-14
what happens if you, instead of "startx" writes the full path "/usr/bin/startx" ?
also, can you boot into recovery mode, and maybe "dpkg-reconfigure xserver-xorg" from there?

edit: did the google warning look like this [http://www.google.com]("http://www.google.com/search?q=phpbb&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial") if it did, then that might be a google error, and not an actual virus

---

### Post by Nils-Johan on 2005-12-14
Sorry for the very late reply.
I am writing a paper for my degree and its a pain.... :)
I havent tried out doing /usr/bin/startx yet but will try a.s.p.

i have tried the dpkg reconfigure xserver-xorg i recoverymode but i get the "command not found" mez. 
Also i get a error mez saying something about bash not found.

edit: yes the google warning was just like that...

---

### Post by vruum on 2005-12-15
aye caramba, this looks really bad... 
or maybe not, if bash is broken or missing, then I'm not sure what to do. it might be as easy as just replacing /bin/bash with a new one from [http://packages.ubuntu.com]("http://packages.ubuntu.com"), but, just to be sure, what happens if you, as a normal user, run the command
"/bin/bash"?

---

