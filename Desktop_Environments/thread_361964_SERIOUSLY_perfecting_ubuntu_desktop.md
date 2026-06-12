---
title: "SERIOUSLY perfecting ubuntu desktop"
date: 2007-02-15
forum: Desktop Environments
---

### Post by elaspeinreason on 2007-02-15
hello everyone, i'd like to thankyou in advance for any help that may be provided.
I recently installed Ubuntu on Dell Laptop that previously worked with XP.
This isnt my first time working with linux, and although im capable , im ignorant as to how to do certain things.

currently I am attempting to install the " Gnome Dock" [http://ubuntuforums.org/showthread.php?t=302570](http://ubuntuforums.org/showthread.php?t=302570)
-i am currently on ** 4. Install Cairo 1.2.6**, thus far i have followed the directions perfectly..why is it that when i attempt to install i get the message : 

everett@caligula-module:~$ /configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc
bash: /configure: No such file or directory

This is not the first time this has happen to me..it seems anytime i try to install ANYTHING it somehow doesnt work..i couldnt even install QUAKE2 from the repositories( i have been having serious trouble grasping the concept of installing on this system..unlike with windows. this is laborious and just plain #*$&@ hard.) 
My system has been lagging quite a bit , and i suspect that i need to optimize my system .* removing what is unneeded. fixing what is loaded at startup..etc *( **second question**) - i would love to optimize my system but installing/uninstalling and knowing just what i can remove could be dangerous.. are there guidelines for this process,,, better yet is there a section where nOobs can get instruction on computing with linux (IE installation/commands/ etc )  ..can someone help me 

i have immense respect for the ideology put forth by the ubuntu movement..but i fear that unless i work out the kinks in my system i will be forced to return to *DEATH*windows.
thank you again ,
frustrated Ubuntu User

---

### Post by JensenDied on 2007-02-15
try 
```
 ./configure <craptons of arguments>
```

./ signifies current directory which is where im guessing your configure script is

/ signifies the root directory which is well, the root of your directory 'tree'

---

### Post by JensenDied on 2007-02-15
okay now that i got that out of the way, it appears you are trying to re-compile alot of things from source as opposed to the pre-compiled versions available in repositories.

might i suggest that if you post more than dell laptop people with similar hardware could point you in directions that might improve tweaks. myself I use a Dell Inspiron 6000 laptop.

---

