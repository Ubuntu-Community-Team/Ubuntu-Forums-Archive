---
title: "ubuntu 11.04 and UT2004"
date: 2011-05-02
forum: Gaming &amp; Leisure
---

### Post by robgraves on 2011-05-02
okay i currently have ubuntu 11.04 natty narwhal installed on my pc and i dug out my old unreal tournament 2004 discs cause i heard it runs natively on linux, well since i've been using linux i haven't bothered to try it until now. 
      anyway, i have it instaled and it boots and the game functions fine, EXCEPT i get no sound, any ideas?

---

### Post by Perfect Storm on 2011-05-02
try launch it with **padsp** command.

---

### Post by robgraves on 2011-05-02
> **Artificial Intelligence said:**
> try launch it with **padsp** command.
sweet that worked, thank you

---

### Post by kvarley on 2011-09-06
Bit late but I had this issue too, padsp suspends pulse audio while you play the game. There is, however, a better solution.

Go into synaptic and search for libopenal - you should find libopenal1.

Right click the libopenal1 package and go to properties, in the new dialog that opens go to the Install Files tab. You will see a bunch of files, look for the library files. They should be something like this:

> /usr/lib/libopenal.so.1
/usr/lib/libopenal.so.1.12.854

Now, you can either symlink the libraries into the ut2004 installation folder or copy them. Copying will ensure it will work even if your library it updated on your system.

Close Synaptic, open up Terminal.

Remove the UT2004 OpenAl library (Change the path accordingly):

> sudo rm /usr/local/games/ut2004/System/openal.so

Copy the OpenAl library install on your system to the UT2004 installation folder (Change the name of the library and paths accordingly):

> sudo cp /usr/lib/libopenal.so.1.12.854 /usr/local/games/ut2004/System/openal.so

Close terminal, fire up UT2004, you'll have sound, go frag some noobs!

(All the information here was taken from: [http://kvarley.co.uk/news/items/no-sound-in-unreal-tournament-2004-heres-your-fix.htm]("http://kvarley.co.uk/news/items/no-sound-in-unreal-tournament-2004-heres-your-fix.htm"))

---

