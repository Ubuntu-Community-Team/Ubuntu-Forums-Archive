---
title: "new to scripts - how to install"
date: 2005-10-27
forum: Desktop Environments
---

### Post by bionnaki on 2005-10-27
can someone show me how to install [this](http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Audio/WOM_audioconverter) script? Never done this before. Thanks!

---

### Post by bionnaki on 2005-10-27
I opened up gedit & pasted the script.
I saved it into ~/.gnome2/nautilus-scripts as "audioconverter"
now what?

---

### Post by funkenstein on 2005-10-27
I would imagine that the commands you'd have to put in are:
```

cd ~/.gnome2/nautilus-scripts
chmod 755 audioconverter
``` This will make the file executable.
After that, you need to pass it some files as arguments, so it would be something like:
```
./audioconverter /path/to/music/file1.mp3 /path/to/music/ffile2.mp3 /path/to/music/file3.mp3
``` The "./" kind of means "Run this as if is was a program" and /path/to/music/files is relative... if you put your music files in ~/music then you could type:
```

./audioconverter ../music/file1.mp3 etc...
``` 
It'll then ask you what you want to convert the file to, after making sure you have everything you need. 

Happy conversion

 I take no responsability if your computer spontaneously combusts/explodes or jihads your ass! :D


(but I'm pretty sure that's what you'd have to do.... :p)

---

### Post by kabus on 2005-10-27
You have to make the script executable :

```
chmod +x audioconverter
```

Then it will show up in the context menu when you right-click on a file.

---

