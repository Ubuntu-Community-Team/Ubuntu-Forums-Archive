---
title: "OpenArena With no GUI?"
date: 2009-03-02
forum: Gaming &amp; Leisure
---

### Post by dennismoore1 on 2009-03-02
does anyone know a way to play openarena without a GUI?

im pretty into linux so im comfortable not using ubuntu or a gui

i have a completely text-based fedora system and i was wondering if i could run open arena straight off of that

does anyone know?

---

### Post by dennismoore1 on 2009-03-02
also, who knows how to set up incoming wi-fi with no gui? xD

---

### Post by Polygon on 2009-03-02
to set up wifi, you need to make sure the proper driver module is loaded on startup, and then double check the output of iwconfig to make sure it created a usable interface (usually ath0 or wifi0 or something like that)

then you need to bring the interface up

sudo ifconfig <interface here> up

connect to the network (if you have a wep network with a key)

sudo iwconfig ath0 essid <essid here> key <key here>

if you dont have a password on your network, you can omit the key entry

if your key is in ascii, do this:

sudo iwconfig ath0 essid <essid here> key s:<ascii key here>

if you have wpa, you better google it as its more complicated

then dhcp the interface:

dhcpcd <interface here>

then it should work

OR

you can just install u/k/xbuntu and have network manager take care of all this for you.......


and to run open arena with no GUI, you should just cd to the directory its in, then run the script that runs the game,the command should be like ./openarena (or whatever the name of the file is called)

im not sure if the game will even work without a gui, cause doesn't it require X?

---

### Post by AdamShumpisxXx on 2009-03-02
I know it might seem off-topic but why deprive yourself of a GUI based OS? Are your hardware specifications very low?

---

### Post by Ozor Mox on 2009-03-03
OpenArena is a first person shooter based off the Quake engine. I have no idea how you expect to play it from the command line. I guess if you install X it might be possible to launch it and the game directly...

---

