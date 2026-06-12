---
title: "trying to run Quake 1 with Darkplaces"
date: 2012-03-12
forum: Gaming &amp; Leisure
---

### Post by Heamogoblin on 2012-03-12
Hi there

I've been trying to get Quake to run on my Lubuntu system using the darkplaces-linux-686-glx method. However i keep getting mixed results.

First the how to guide i'm following says that i can type "Games/quake$ darkplaces-linux-686-glx" into the terminal and it will run. But this is actually what i get.

"Games/quake$ darkplaces-linux-686-glx
darkplaces-linux-686-glx: command not found"

If i go the gui route, i'm asked it i want to execute the file or execute in terminal. The latter doesn't nothing. But selecting the first actually will try loading Quake. 

I thought i'd got it working at one point, i was actually playing quake. However on reboot it tried getting back in to the game and Darkplaces proceeded to tell me i had files missing. I'll quit out of darkplaces, mess around trying to boot via terminal ect..and then i try just executing the icon and suddenly i'm in the game, it's found all the files it needs.

Does anyone have a clue what is going on?

---

### Post by Brebs on 2012-03-12
Sounds like you should prefix that command with ./

i.e.

./darkplaces-linux-686-glx

Which means to run the file which is in the *current directory*, rather than look in $PATH.

If that doesn't help, then show your files and directory structure.

---

### Post by Heamogoblin on 2012-03-12
That seemed to work..thanks! i'm still learning about the terminal and how to use it. 

Can i trouble you with one more question?

How would i make an icon to run this command?

Presently i have this in the icon script

"Exec=/home/haemogoblin/Games/quake/darkplaces-linux-686-glx
StartupNotify=true
Terminal=true
MimeType=x-directory/normal;inode/directory;"

---

### Post by Brebs on 2012-03-12
First write a script that runs the game. Then change the Exec= line to point to that script.

Remove your useless MimeType= line.

To create the script, use e.g.:
```
mkdir ~/bin
echo "cd ~/Games/quake/ && exec ./darkplaces-linux-686-glx" > ~/bin/darkplaces
chmod 750 ~/bin/darkplaces
```

---

### Post by Heamogoblin on 2012-03-13
i've never actually made a script before.

Can i trouble you to explain to process going on in the above commands?

---

### Post by Brebs on 2012-03-13
Well, my script above creates the directory, creates the script in that directory, then makes the script executable.

---

### Post by Heamogoblin on 2012-03-13
And then i link the icon with the script?

Thank you, it's really nice to learn more about the terminal. I use it, but i dont USE it, if that makes any sense.

---

### Post by HolgerB on 2012-03-15
Heamogoblin,

> 
And then i link the icon with the script?

You create a shortcut to this script, add the icon of your choice to the shortcut and you are set :)

> 
Thank you, it's really nice to learn more about the terminal. I use it, but i dont USE it, if that makes any sense.

I guess I get your picture but in the end it can never hurt if you understand what is driving your Ubuntu beneath the GUI. Similar to Windows Users which still should know about how a command shell works. 

Or if you like another picture more: For driving a car you must not be your own technician but at least have some common understanding how things work (checking air in tires, checking oil, fill up the gas) :)

HTH,
Holger

---

### Post by sweet28 on 2012-03-15
Thanks Im learning too!

---

### Post by Heamogoblin on 2012-03-17
Well the good news it, i now have Quake running on my little Lubuntu system and it runs great.

I am now hitting a problem with mods, i only want the one to work which comes in it's own dir. i used to play it back in 97 and i would really like to have a mess around on it.

In windows the command would be

"Quake -game startrek +map ncc1701D

How does this translate using darkplaces

in the root of my Quake Dir it looks a little like this

-Quake
--ID1
--startrek

This is how the zip told me to install it, NOT inside the ID1 dir.

i've tried altering the script in the icon but had not success. I've also look in game under the mods section. It shows the startrek mod with the OFF/ON option. Selecting ON will throw me out of the game.

Cheers
James

---

### Post by Brebs on 2012-03-17
> **Heamogoblin said:**
> Quake -game startrek +map ncc1701D
cd ~/Games/quake/ && darkplaces -game startrek +map ncc1701D

---

### Post by Heamogoblin on 2012-03-17
Breb - when ever i have tried to run darkplaces through the terminal, it doesn't work for it. If i click on the icon and tell it to execute, it runs. But via terminal it tells me "unknown command"

I've tried variations of the -game startrek +map ncc1701d command in terminal and in the icon script..DP will either just load quake as usual or tell me it can't find a basedir. I've tried using "gamedir startrek" in the quake console. The screen will refresh and when i try "map ncc1701" it tells me it cant find a map of that name :S

i'm properly scratching my head lol

---

### Post by Heamogoblin on 2012-03-17
:~/Games/quake$ darkplaces-linux-686-glx -game startrek +map ncc1701D
darkplaces-linux-686-glx: command not found

---

### Post by Brebs on 2012-03-17
Argh, for the sake of sanity, create ~/bin/darkplaces which contains:

cd ~/Games/quake/ && exec ./darkplaces-linux-686-glx "$@"

---

### Post by Heamogoblin on 2012-03-17
Perhaps it's through my lack of knowledge about the terminal, but i'm afraid i'm not following you Brebs. Sorry mate :(

---

### Post by Heamogoblin on 2012-03-18
Only way I've found round it, is playing via dosbox. As I know Dos better then I do Linux terminal

---

### Post by HolgerB on 2012-03-18
Errrr.....Mate, are you serious ?
How complicate can it be?

1) Open a terminal
2) Change in the directory where you installed / extracted darkplaces to:
cd /home/your-user/darkplaces
3) check if the darkplaces binaries are there:
ls dark*
4) Launch the corresponding darkplaces binary (as described above)

DOSBox means a big performance penalty. A typical dual core with > 2.5GHz has a hard time emulating a faster Pentium from back then (e.g. 133, 150).

---

### Post by Heamogoblin on 2012-03-18
Right have the file launching via terminal using the "./" before the file name.

However it's still not picking up the mod with

./darkplaces-linux-686-glx -game startrek +map ncc1701D

PSOFTRAST available (SSE2 instructions detected)
execing quake.rc
execing default.cfg
execing config.cfg
couldn't exec autoexec.cfg
SpawnServer: no map file named maps/ncc1701D.bsp
Client using an automatically assigned port

---

### Post by Heamogoblin on 2012-03-18
I've sorted it!! i had forgotten about linux being case sensitive when i comes to files,folders etc.

Xachiever unzipped the files and all of the folders ended up named in upper case MAPS/PROG/SOUND.

As it kept feeding back in the terminal that it couldn't locate the map, i suddenly realized about case sensitivity :P

---

