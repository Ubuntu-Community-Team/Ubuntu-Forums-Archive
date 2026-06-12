---
title: "MP3 preview in Nautilus!"
date: 2005-12-27
forum: Desktop Environments
---

### Post by anil_robo on 2005-12-27
I think I just discovered something! I rest my mouse pointer over an MP3 file shown in Nautilus, and it starts playing by itself! No clicks required - just keep your pointer over the mp3 file icon for 1 second and it plays! I take the mouse pointer off it, and the playback stops!

This is so nice! I never knew I don't have to double click a file to preview it :) Try it today, and let me know if it works for everyone! :)

Ubuntu is amazing! :)

---

### Post by Pablo_Escobar on 2005-12-27
Yep :) I was kinda confused when I discovered it some time back :)
Good feature :)

---

### Post by meborc on 2005-12-27
yep... also works on desktop... but its kind of annoing when you just happen to have a mp3 in your desktop and your mouse goes over it... :rolleyes: but still kick-ass

---

### Post by audax321 on 2005-12-27
Actually it doesn't work for me :( 

I disabled it when I initially installed Gnome, but now after re-enabling it in Nautilus (via Edit > Preferences) it doesn't work. Any idea why?

I can play MP3s in Rhythmbox, Totem, and Beep fine though...

EDIT: Fixed it, the mpg321 program from Universe needs to be installed for it to function...

---

### Post by Stoff on 2006-01-10
i have just checked this function with my newly installed ubuntu breezy version. disableing and reenableing works properly on my system.
maybe your player doesn't work. but which player is used for the preview?

christoph

---

### Post by Gandalf on 2006-01-10
You need to install mpg123 for that
```

sudo apt-get install mpg123

```

---

### Post by Stoff on 2006-01-10
i haven't installed mpg123, however, the mp3 preview works.
so how can i find out which player nautilus currently uses for previews?

christoph

---

### Post by Stoff on 2006-01-10
oddly enough, the preview works only with files on my desktop. if i rest the mouse pointer on a mp3 file in nautilus, nothing happens. 

in the meantime i have installed mpg123. but it does not show the desired effect.

christoph

---

### Post by Gandalf on 2006-01-10
I know that mpg123 is what is used for such needs, try to launch it first
(Alt + F2 ---> mpg123 )

---

### Post by Stoff on 2006-01-10
[QUOTE=Gandalf]I know that mpg123 is what is used for such needs, try to launch it first
(Alt + F2 ---> mpg123 )[/QUOTE]

i tried it out, without success. again, only the desktop preview works (with and without mpg123), but not the nautilus preview

christoph

---

### Post by linkunderscore on 2006-01-10
It is a really nice feature. The only problem is that there is a slight bug with it. If you have your mouse over an mp3 and it starts playing then you somehow manage to close nautilus before is stops playing the song...the song keeps playing in the background until you killall nautilus.

---

### Post by mlalkaka on 2006-01-10
For all people who were having troubles getting the MP3 preview feature to work, try installing the mpg123-esd package:

```
sudo apt-get install mpg123-esd
```

The mpg123 package did not work for me, but mpg123-esd worked. This makes sense since GNOME and Nautilus use ESD for audio playback. You can have mpg123 and mpg123-esd installed concurrently with no conflicts.

Hope this helps :)

This feature *is* awesome IMO. (Another feature that appeared on GNU/Linux and Unix before MS Windows. And, as expected, now Windows Vista will also have this feature)

---

### Post by brian g on 2006-04-12
[QUOTE=linkunderscore]It is a really nice feature. The only problem is that there is a slight bug with it. If you have your mouse over an mp3 and it starts playing then you somehow manage to close nautilus before is stops playing the song...the song keeps playing in the background until you killall nautilus.[/QUOTE]i've run into this issue a lot! it' sucks. usually i can get away with killing mpg123, but sometimes everything is so frozen up that i can't even open my system monitor ](*,)

---

### Post by strabes on 2007-09-03
You also need to install the package "vorbis-tools" in feisty.

---

### Post by svtfmook on 2007-09-03
works for me, but not on wma files

---

### Post by PmDematagoda on 2007-09-05
Linux just keeps getting better and better for me, but while I can preview .mp3, I can't preview videos does anyone know why? I already tried setting the minimum file size to 1GB and nothing happened. I tried with both .avis and .mpegs.

---

### Post by light50 on 2008-02-10
Worked for me on the desktop and in nautilus - but only when files are viewev as icons *not as a list*....chur!

---

### Post by Man of Wax on 2008-02-10
I've installed all the things you wrote but nautilus preview doesn't work... :confused:

---

