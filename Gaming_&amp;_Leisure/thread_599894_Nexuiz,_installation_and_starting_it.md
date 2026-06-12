---
title: "Nexuiz, installation and starting it"
date: 2007-11-01
forum: Gaming &amp; Leisure
---

### Post by techno-mole on 2007-11-01
ok, so ive downloaded nexuiz, and according to the instructions you can just unzip it and then run it.
only this doesnt seem to be working for me, i can unzip it ok, but when it comes to running it all i get is a black screen saying nexuiz and loading, and thats all it does.
so what am i missing ?
there is an .exe file, but that wont run it either.
cheers in advanced for any help.

---

### Post by ddrichardson on 2007-11-01
nexuiz is in the repos, you can install it with sudo apt-get install nexuiz. I was playing it earlier. It does appear to sit at a black screen when loading from time to time though.

---

### Post by techno-mole on 2007-11-01
i did install it from the repo's but it would stick on the loading screen and thats as far as i could get with it, maybe ill try again.
cheers

---

### Post by ddrichardson on 2007-11-01
I'm a little confused as to how you wound up with a zip and and exe when you obtained it from apt?

---

### Post by techno-mole on 2007-11-02
after i couldnt get it running from the repo's i went to the nexuiz website, and downloaded it from there, which is where i got the .exe from.
anyway i couldnt get it running that way (which is why i posted) i went back to the repos and installed it again from there, and it worked first time :confused: the only problem i have now is that for some reason when im in a game im constantly running forward (kind of like when you press a key twice and it sticks) so i need to solve that problem.
cheers

---

### Post by TheThinker on 2007-11-02
> **techno-mole said:**
> ok, so ive downloaded nexuiz, and according to the instructions you can just unzip it and then run it.
only this doesnt seem to be working for me, i can unzip it ok, but when it comes to running it all i get is a black screen saying nexuiz and loading, and thats all it does.
so what am i missing ?
there is an .exe file, but that wont run it either.
cheers in advanced for any help.

Are you running on an Athlon 64 architecture, or an i386? It could be that you've been running the wrong executible that's meant for a different architecture. Usually they're named with "64" or "i386" toward the end to specify this crucial difference.

If I'm right, I'd delete the settings file that Nexuiz generates in your Home folder. Just make sure your file-browser is set to see "hidden files/folders" and find the folder named ".nexuiz" and delete it. This will reset the settings so that you can try my suggestion (which will subsequently create a new settings file). If you don't, Nexuiz will just stick to the incorrect settings-file it generated when you used the wrong executible file and crash again.

---

### Post by Sockerdrickan on 2007-11-02
Why install Nexuiz?

[www.nexuiz.com](www.nexuiz.com) get the official and just play without install \\:D/

---

