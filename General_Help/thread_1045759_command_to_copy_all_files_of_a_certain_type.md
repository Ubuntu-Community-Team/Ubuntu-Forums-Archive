---
title: "command to copy all files of a certain type?"
date: 2009-01-20
forum: General Help
---

### Post by PoopyTheJ on 2009-01-20
Is there a command to copy all files of a certain type to a directory? I want to copy all my mp3 files to a directory and I don't really need a directory structure I just want them all in that directory. Thanks!

---

### Post by snova on 2009-01-20
```
find /place/where/your/music/is -name '*.mp3' -exec mv {} /place/to/put/them \;
```

---

### Post by jerome1232 on 2009-01-20
--edit-- correction cp can't do that, find works, tested it just now.

---

### Post by PoopyTheJ on 2009-01-20
hmm those did not work. In windows I could do a search and then highlight everything and choose copy and paste. I can't copy and paste out of the Ubuntu/Gnome search function. I have all my mp3's in /Music now, however they're all in different directories within Music. I want to search for all mp3 files and copy them into one lump directory so I can setup a music station to listen to at work. the second command cp -r /source/folder/*.mp3 /target/folder/ gave me a can't stat /Music error and the other command just left me at a blank > cursor.

---

### Post by snova on 2009-01-20
It's probably the leading slash. I hope your music isn't located in /!

A leading slash will look in the root directory, and there shouldn't be anything there of yours.

For simplicities sake, lets assume you want to move them to a folder on your desktop:

```
find ~/Music -name '*.mp3' -exec mv {} ~/Desktop/folder \;
```

~ is expanded to your home directory.

---

### Post by ratmandall on 2009-01-20
> **PoopyTheJ said:**
>  I have all my mp3's in /Music now, however they're all in different directories within Music. I want to search for all mp3 files and copy them into one lump directory 

Run this
```
cd /home/$USER/Music; mkdir mp3dump/ ; cp */*.mp3 /home/$USER/Music/mp3dump/
```
It will copy all the mp3's in your Music folder to a directory called "mp3dump" in /home/$USER/Music

EDIT:If you have a lot of mp3's then this will seem as if it's frozen at the command line, but it's just taking a while to copy them over.

---

### Post by snova on 2009-01-20
> **ratmandall said:**
> Run this
```
cd /home/$USER/Music; mkdir mp3dump/ ; cp */*.mp3 /home/$USER/Music/mp3dump/
```
It will copy all the mp3's in your Music folder to a directory called "mp3dump" in /home/$USER/Music

Assuming his music is not nested any furthur than one folder down... sadly, **/*.mp3 globbing doesn't work in your typical Bash shell.

Otherwise that'd be perfect.

---

### Post by ratmandall on 2009-01-20
> **snova said:**
> Assuming his music is not nested any furthur than one folder down... sadly, **/*.mp3 globbing doesn't work in your typical Bash shell.

Otherwise that'd be perfect.

I'm not quite sure what you mean? is that not what the OP wanted?

To copy all the mp3's in sub-directories of Music/ to a separate folder.

---

### Post by snova on 2009-01-20
> **ratmandall said:**
> I'm not quite sure what you mean? is that not what the OP wanted?

To copy all the mp3's in sub-directories of Music/ to a separate folder.

I mean, if his music is nested *two* directories down, it won't work, such as "directory/subdir/music.mp3". The glob accounts for "directory/music.mp3" but doesn't go any deeper than that.

So it might work, but it depends on his particular directory structure.

---

### Post by snova on 2009-01-20
Or, hey, combine 'em and get the best of both. :P

```
cd /home/$USER/Music; mkdir mp3dump ; find -name '*.mp3' -exec cp {} mp3dump \;
```

There, that should work.

---

### Post by ratmandall on 2009-01-20
> **snova said:**
> I mean, if his music is nested *two* directories down, it won't work, such as "directory/subdir/music.mp3". The glob accounts for "directory/music.mp3" but doesn't go any deeper than that.

So it might work, but it depends on his particular directory structure.

Oh. I understand now, time to get back on topic.

*Twiddles thumbs*

---

### Post by sedawk on 2009-01-20
Again a command line solution using find and assuming target directory /home/myself/mp3all exists:
```

find /Music -name \*.mp3 -print0 |xargs -r -0 cp -t /home/myself/mp3all/

```

This will overwrite songs with the same name, e.g. "power_of_love.mp3".

If you want the subdirectory structure to exist also in the
new directory /home/myself/mp3all you have to use another
tool combo, e.g. find+cpio. I don't use it very often, so
I can give no example without further testing ...

---

### Post by PoopyTheJ on 2009-01-21
find ~/Music -name '*.mp3' -exec mv {} ~/Desktop/folder \; that worked! Thanks guys! I just got done with a reinstall now I nedd to figure out why windows7 and xp won;t boot but that's in another thread...

[http://ubuntuforums.org/showthread.php?t=1046904](http://ubuntuforums.org/showthread.php?t=1046904)

---

