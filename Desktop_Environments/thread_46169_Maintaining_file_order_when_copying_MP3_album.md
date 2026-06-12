---
title: "Maintaining file order when copying MP3 album"
date: 2005-07-03
forum: Desktop Environments
---

### Post by hamiltonlight on 2005-07-03
Hello Ubuntians, 

I'd like to say that I'm a relative Linux newbie. I've tried a few different distros, Suse and Mandrake primarily. Ubuntu is the one that has made me ditch XP for good, it allows me to learn Linux at my own pace and things just work for everyday stuff. Keep up the good work!! 

I'm digging deeper into the OS everyday but there is something that I cannot find the solution to. I have an MP3 player that uses SD cards. When I copy a MP3 album onto the card it will copy the tracks in a random order. The MP3 player then plays them in the order they are copied. This did not happen under the previous OS if I remember correctly. Is there something obvious that I have missed?

Also, when I delete the albums from the SD card they are placed into a .Trash_Hamilton folder. I then have to open this folder and delete them again to properly remove them. Can this be corrected so that the first delete will remove the files from the card?

I hope someone can help me or point me in the right direction. Thanks in advance.

Hamilton

---

### Post by Bo Rosén on 2005-07-03
[QUOTE=hamiltonlight]Hello Ubuntians, 

I'd like to say that I'm a relative Linux newbie. I've tried a few different distros, Suse and Mandrake primarily. Ubuntu is the one that has made me ditch XP for 
[/quote]
Welcome to Ubuntu and the community! 
> 
album onto the card it will copy the tracks in a random order. The MP3 player then plays them in the order they are copied. This did not happen under the previous OS if I remember correctly. Is there something obvious that I have missed?

I don't have an mp3 player (donations welcome), so don't really know what I'm talking about, but how you name your files may play a part. I always begin my file names with the track number. Currently playing 08 - Emm Gryner - your sort of human being.mp3. Some (most) music players sort the songs based on the id3 tag, but the file system doesn't.

> 
Also, when I delete the albums from the SD card they are placed into a .Trash_Hamilton folder. I then have to open this folder and delete them again to properly remove them. Can this be corrected so that the first delete will remove the files from the card?

When you delete a file it is first placed in the trash can. This can easily be found in the bottom right corner of the screen - right click to bring up a menu to empty permanently or restore files. isn't this pretty much the same as in windows and mac OS? I don't think you can have different behaviour for different folders, but you can add a command to the right-click menu to remove a file completely, bypassing the trash folder. Start nautilus (Open you home folder) go to Edit --> Preferences --> Behaviour and check the option that says something like "Include a command Remove that bypasses the trash can"
Then just right click any files you want permanently and irrevocably deleted and use this command.
I don't use the English language version, but it should be reasonably close.
Good luck

---

### Post by hamiltonlight on 2005-07-04
Thanks for the reply.

The annoying thing is that the filenames are all in a logical order. I like to name them beginning with a leading zero so they all list properly. They all appear in order under nautilus. When playing the album XMMS plays them in the correct order. 

Its when I copy the files across to the sd card that the ordering is not taken into account. 

Apologies, I should have been more specific regarding the trash can. Deleting the files places the folders etc into a trash can on the sd card and not into the trash can on the bottom right of the desktop. I will try the suggestion you gave.

Thanks again.

Hamilton

---

### Post by ritger on 2005-07-04
In Nautilus Preferences there's an option to include a `Delete' command next to the Move to Trash command. This will get rid of the file without trashing it first. 

As for the mp3 copying problem, i have the same problem. You could drag the files on the SD card one by one in order, or just do what i do and live with it.

---

### Post by kblood on 2005-11-10
I have exactly the same problem, the files get copied in random order, and my mp3 player plays them in filesystem order, so... albums get "shuffled"! A bit annoying...

I can live with it, yes, but it's not so pretty.

So if anyone has an idea, besides copying file by file, I would love to hear it! :KS

And yes, my files also start with 01... 02... 03........ ... .. .. 10... 11... 12... so they should be ordered logically.

---

### Post by poptones on 2005-11-10
Then just make a little script to copy the files one by one...

for ALL in "`ls -1`";do cp "$ALL" /mnt/mysd/card;done

You could make a "outbox" folder on your desktop and copy links (middle button, click and drag) to the folder, then make a launcher for the script above on your taskbar. Copy the (links to) the albums you want to transfer, then click the launcher. Once the files are copied you can safely delete the links woithout affecting the files themeslves and without taking forever to copy actual files.

Don't any of the music players have built in software to handle this sort of thing?

---

### Post by kblood on 2005-11-11
That script looks pretty good, but any chance of it being recursive? That is, copying complete folder structures?

By the looks of it, it isn't, but I might be wrong, and I can't test it right now... (though I will, for sure)

---

### Post by hashimoto on 2005-11-11
There is also a (cli) program called fatsort which is made just for the purpose. Install thru Synaptic/apt-get. 

To me fatsort doesn't work though, claiming that I don't have rights or something. Funny thing is that I can copy to/delete from the palyer just fine. If someone could help with this, I would appreciate.

---

