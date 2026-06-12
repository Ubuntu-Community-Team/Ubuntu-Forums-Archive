---
title: "scripting help"
date: 2005-03-28
forum: Desktop Environments
---

### Post by puelly on 2005-03-28
I would like to write a short script to go thru all the files in the /usr/share/applications/kde/ directory and add "OnlyShowIn=KDE;" at the end of the files

i know i have to use *echo >>"OnlyShowIn=KDE;"* but I don't know how to loop through all the files.

Any help would be appreciated.  Thanks.

---

### Post by cwaldbieser on 2005-03-28
The following script echos the name of every file in the directory.

```

for file in /usr/share/applications/kde/* 
do 
     echo $file
done
```

I am not 100% sure I understand what you want to do, but if you just want to append the line "OnlyShowIn=KDE;" to the end of the files, then I would try:

```

for file in /usr/share/applications/kde/* 
do 
     echo 'OnlyShowIn=KDE;' >> $file
done
```

Online help for the bash shell can be accessed by typing 'help' at the prompt.  You can also get help on individual commands (e.g. 'help for').

---

### Post by puelly on 2005-03-29
[QUOTE=cwaldbieser]The following script echos the name of every file in the directory.

```

for file in /usr/share/applications/kde/* 
do 
     echo $file
done
```

I am not 100% sure I understand what you want to do, but if you just want to append the line "OnlyShowIn=KDE;" to the end of the files, then I would try:

```

for file in /usr/share/applications/kde/* 
do 
     echo 'OnlyShowIn=KDE;' >> $file
done
```

Online help for the bash shell can be accessed by typing 'help' at the prompt.  You can also get help on individual commands (e.g. 'help for').[/QUOTE]
 thank you. that looks exactly whay I want to do.  I'll try it and let you know how it goes.

---

### Post by puelly on 2005-04-10
thanks again for your help. here's a copy of the script that I used below.  works like a charms.  Looks like I'll have to run it everytime I update my system but makes my menus look so much cleaner when I am in GNOME.

```
#!/bin/bash

for file in /usr/share/applications/kde/*
do
     echo 'OnlyShowIn=KDE;' >> $file
done

```

Thanks again.

---

