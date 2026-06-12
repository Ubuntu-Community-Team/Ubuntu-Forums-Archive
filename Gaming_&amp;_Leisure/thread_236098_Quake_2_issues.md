---
title: "Quake 2 issues"
date: 2006-08-14
forum: Gaming &amp; Leisure
---

### Post by zugu on 2006-08-14
I'm trying to have Quake 2 working on Dapper.
So I did apt-get install quake2. It installed some packages and dependencies. Now I knew that I would be needing the original CD (I have it), but never knew where to start from.

Package quake2 created a ~/.quake2 directory. I tried to run the game, but it said it needed some data files. I figured out it's the original CD I have to install. I started the setup.exe with wine and installed the game in some other directory. Then copied all the files from there to my ~/.quake2 dir. Then ran the game. Surprise, it worked!

Next step was to connect to an online server. Nowadays, almost all servers require clients that run version 3.20 of the game. Running the "version" command in Q2 returned something like "ubuntu-gnu-linux0.3" (quoting from memory, not the exact value, but it was definitely not sying "3.20").
I thought about connecting and see if it works. Unfortunately, the server was using some maps and models my client did not have. The logical step would have been automatic retrieval of the missing files from the server. However, the client reported that the files were not on the server. This is very strange, as on Windows a fresh Q2 install from the same CD with the 3.20 patch would be missing the same files, but would nevertheless retrieve them from the server.

I thought maybe the client is not updated to the 3.20 Linux equivalent version. I tried to alien the rpm from id software's ftp, and when installing it with dpkg it said that my Quake installation will be downgraded. So I concluded that whatever installs from the repos when I "apt-get install quake2" has to be the latest version.

I heard it all about Q2 - it's open source, it works on various distros etc., etc. - now I just want it to work on my Ubuntu.

I forgot something: I tried to run the wine-installed Q2 in wine - no success: it says it's missing some important files.

Any clue where to start from is welcome.

---

### Post by HAARP on 2006-08-14
The version in the repos is strange. It's not 3.20 (latest Windoze), nor 3.21 (latest Linux). Something between, and I've got no clue what.
I'd recommend the [Loki Installer](http://liflg.org/?catid=6&gameid=55), however it's some tweaked version of 3.21, and incompatible with 3.20.
Use the iD Software one. It's 3.20. The repos one is newer, yes. But it sucks.
I've never got the iD one to work tho...the actual executable must be executed with root rights!?

---

