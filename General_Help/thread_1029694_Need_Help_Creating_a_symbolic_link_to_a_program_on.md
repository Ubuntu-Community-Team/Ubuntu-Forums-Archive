---
title: "Need Help Creating a symbolic link to a program on Windows HDD"
date: 2009-01-03
forum: General Help
---

### Post by zyxyellowxyz on 2009-01-03
Apparently terminal doesn't like it when the folder name has spaces in it, or atleast that's all I can figure out at the moment.

I want to create a symbolic link to program I have installed on my windows hard drive just so I don't have to reinstall it on this hard drive.

I know the command goes like this:

```
sudo ln -s /where/the/file/or/folder/is /where/you/want/the/link
```

The problem I run into is when I have everything typed out like I think is correct, I ended up creating a lot of little broken links.

This is what I ran:
```
sudo ln -s /media/disk/Program Files/World of Warcraft/Launcher.exe /home/susan/Desktop/
```

I ended up creating broken links to "program", "world", "of", and "warcraft."

What do I need to do so I don't end up doing that again?

---

### Post by wmdiem on 2009-01-03
add a \ in front of the spaces in the path 
      ^ that's a backslash
so :
World\ of\ Warcraft/Launcher.exe

---

### Post by zyxyellowxyz on 2009-01-03
Thank you! That helped a lot. It works now

---

### Post by sleepyjon on 2009-01-03
You can also use tab complete or double quotes.

---

### Post by lswb on 2009-01-03
Surround any filenames that contain spaces in quotes like this:
```

sudo ln -s "/media/disk/Program Files/World of Warcraft/Launcher.exe" /home/susan/Desktop/

```

Another way is to "escape" the space by using a backslash
```

sudo ln -s /media/disk/Program\ Files/World\ of\ Warcraft/Launcher.exe /home/susan/Desktop/

```

Certain other characters that may appear in filenames may also need to be in quotes or escaped when working in the shell. Some of these are  # & ( ) \  and a few including $ and ! must sometimes be quoted _and_ escaped.

man bash for the gory details and scroll down to the QUOTING section

---

