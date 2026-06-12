---
title: "Save games lost on steam ???"
date: 2015-08-13
forum: Gaming &amp; Leisure
---

### Post by rob141 on 2015-08-13
Hello, i have installed steam and i am using the same account as in windows so all my game data should be there right ?  Is it normal that i have to re-install my games and also that i have lost my save games ? I have just started dead island and all i can do is start a new game but i dont want to do that. What can i do to get my save games back please ?

---

### Post by mystics on 2015-08-14
If I'm understanding things correctly, you've installed and played these games in Windows and are wondering why you have to re-install and where the saves went?

As for re-installing, that is standard. Even if you are on the same computer and dual-booting, the games you installed in Windows are on the Windows partition. As far as Linux, which is on a separate partition, is concerned, they aren't installed. It's like they're on a separate computer. 

This is a similar issue with saved games. They are all saved on the Windows partition. However, you might be able to get the save files over to Linux. If the save file still exists on Windows, you can try to mount it and transfer the files directly, or you could always jump back over to Windows, use any method for transferring files from one computer to another (USB, cloud storage, email), place the file in there, jump back over to Linux, and place the save file where it belongs.

---

### Post by pietro4 on 2015-08-14
yes, because you instaler steam in two os, indentical a instalar steam in two different computer.... :)

---

### Post by pietro4 on 2015-08-14
for the saved game is in database for steam and recover and start game. ;)

---

### Post by rob141 on 2015-08-14
Thank you veru much [COLOR=#000000]Mystics and pietro4 for your replies. Yes i have a dual boot. My windows partition are already mounted in ubuntu. I have found where are the save files in my windows partition but now i can seem to find where can i copy that folder or file into steam on ubuntu ? Witch folder does steam saved the games on ubuntu so i can just copy and paste my save file ?[/COLOR]

---

### Post by mystics on 2015-08-14
Well, pietro4 did bring up something I forgot: Steam cloud. I haven't played Dead Island myself, but I'm pretty sure that it does take advantage of it. If you have any saves there, you may just need to set up Steam to get saves from the cloud.

However, if that isn't an option, then you should be able to find Steam-related stuff in

~/.steam

The '~' stands for your home directory, which is the same place the Documents and Downloads folders are. The '.' before steam indicates that it is a hidden file, so you'll need to show hidden files in order to find it. Ctrl-H should help you see these. From there, Steam should, to my knowledge, be set up the same as it is on Windows.

Unfortunately, I can't give much more information than that. As far as I know, Steam isn't consistent in where places save files, and having not played Dead Island myself, I can't search around to get specifics.

---

### Post by efflandt on 2015-08-15
If you recently installed steam, the game files are probably in  ~/.steam/steam/steamapps/common/, although, on my where steam was  installed in 12.04 and copied over to 14.04 they are actually in  ~/.local/share/Steam/SteamApps/common/. But the hidden directory  ~/.steam/ should give you a clue, either with a "steam" directory there  or symbolic links (like Windows shortcuts) to where they actually are.

Games that use the Steam Cloud (generally games with a multi-player mode) automatically have your achievements, items, etc. when you install the game in any system or OS the game is compatible with. That was the case when the Linux partition at the far end of my drive began failing and I installed steam and played a multi-player game in Win7 (my achievements and items were there automatically) until I got a new drive (then shrinking Win7 partition before cloning it to new drive to make more room for Linux Steam games).

But  games that do NOT use the Steam Cloud (typically single player games or  games under development) are inconsistent about where they keep their  save files (very likely a different path than in Windows unless a Windows game running under wine). Some Linux  Steam games might keep their saves in their own directory, some might in  a hidden directory (leading dot) in your home directory, and at least  one game I have has its directory for its saves in ~/Documents/. So you might  not know where a game saves its save games in Linux until you save game status in Linux.

---

### Post by rob141 on 2015-08-17
Thank you so much, with the right path of where are stock the games on steam, i was able to copy and paste the DeadIsland folder. I have not tested it yet but i am sure it will work so again, thank you all very much ;)

---

### Post by oldrocker99 on 2015-08-18
For what it's worth, in my dual-boot days, I bought Torchlight II for Windows. When it came out for Linux, my old Windows Steam saves were there, allowing me to pick up where I had left off.

---

