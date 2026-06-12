---
title: "Add parent dir to child dir's name"
date: 2009-01-17
forum: General Help
---

### Post by brdlvelixir on 2009-01-17
So, I have a bunch of mp3 albums in my music folder, organised by artist, then in each artist's folder are all that artist's cd's. I want to put all the album folders directly in the music folder **after appending the artist name to each of their album's dir name.** Is there a program or script that does this? I've used pyRenamer but don't see an option for this.. Here is my dir structure:

~/music/artist_1/album_1
~/music/artist_1/album_2
~/music/artist_1/album_3

~/music/artist_2/album_1
~/music/artist_2/album_2
~/music/artist_2/album_3

where I want:

~/music/artist_1-album_1
~/music/artist_1-album_2
etc...


Thanks, any help is appreciated.

---

### Post by sedawk on 2009-01-17
What I would do is create a script that doesn't rename/move the directories,
but only gives a list of the commands that need to be executed. That list
can then be reviewed before executing it!

The output of the script should be something like this:
```

mv artist_1/album_1 artist_1-album_1
mv artist_2/album_1 artist_2-album_1

```

This might give you the list:
```

cd ~/music
find . -type d -print |while read FOO;do
echo "mv $FOO ${FOO%/*}-${FOO##*/}"
done |tee >rename_music.lst

```

After checking that list and removing all "broken" lines you
can go to the music directory and execute it
```

cd ~/music
. ./rename_music.lst

```

Carefully review the list before executing and
do at your own risk!

---

### Post by blackened on 2009-01-17
Pretty sure you can do what you're asking with easytag. It can also do id3 tags at the same time if you want, or strictly use it for batch renaming. It's available in the repos:

```
sudo apt-get install easytag
```

---

### Post by brdlvelixir on 2009-01-18
sedawk, I wish I knew how to script, it would make things so much easier and I wouldn't have to come on here asking for ways to do things... and I could fix code that probably needs a few minor tweaks... but, I can't, and I have no clue how your code (almost) works. For testing, I copied two bands' folders to a 'test' folder. They are insomnium and mors principium est. insmnium contains three folders and mors princ. has one. Here's what what was in the rename_music.lst file that was generated:

> mv . .-.
mv ./insomnium .-insomnium
mv ./insomnium/above the weeping world ./insomnium-above the weeping world
mv ./insomnium/since the day it all came down ./insomnium-since the day it all came down
mv ./insomnium/in the halls of awaiting ./insomnium-in the halls of awaiting
mv ./mors principium est .-mors principium est
mv ./mors principium est/the unborn ./mors principium est-the unborn
mv ./mors principium est/inhumanity ./mors principium est-inhumanity

when I executed this file here's the output I got:

> user@user-desktop:~/test$ ./rename_music.lst
mv: cannot move `.' to `.-.': Device or resource busy
mv: target `world' is not a directory
mv: target `down' is not a directory
mv: target `awaiting' is not a directory
mv: target `est' is not a directory
mv: target `unborn' is not a directory
mv: target `est-inhumanity' is not a directory

So some bugs I see are that its trying to rename the working dir, which is okay because it can't do it anyway, but the code needs to provide quotation marks around the titles. Here's how my folders were renamed:

insomnium became .-insomnium
and
mors principium est didn't change.
All albums inside these folders also remained the same.

Any quick fixes to the code?

As for easytag, I like to try things the hard way first... I'll check it out though

---

### Post by mssever on 2009-01-18
> **brdlvelixir said:**
> sedawk, I wish I knew how to script, it would make things so much easier and I wouldn't have to come on here asking for ways to do things... and I could fix code that probably needs a few minor tweaks... but, I can't, and I have no clue how your code (almost) works.
<snip>
Any quick fixes to the code?As you suspected, sedawk's code is almost correct, but it can't handle files and directories with spaces in the name. Here's sedawk's code modified (notice the change in the quotes on the echo command):
```
cd ~/music
find . -type d -print |while read FOO;do
[ "$FOO" -ne . ] && echo "mv '$FOO' '${FOO%/*}-${FOO##*/}'"
done |tee >rename_music.lst

```WARNING: I haven't run sedawk's code, and it does more parameter substitution than I'm used to, so I'm not confident that the quotes were the only problem; however, it's probably correct now.


EDIT: From re-reading your output, it appears that the script was also picking up the current directory. I added a test for that to exclude the current directory.

EDIT 2: After more re-reading and seeing more incorrect output from sedawk's code, I decided to write another script from scratch, which might be easier to debug:
```
#!/bin/bash
cd ~/music
for i in *; do
  [[ -d "$i" ]] || continue
  for j in "$i"/*; do
    mv "$j" "$i-$(basename "$j")"
  done
done
```

---

### Post by brdlvelixir on 2009-01-20
> **mssever said:**
> 

EDIT 2: After more re-reading and seeing more incorrect output from sedawk's code, I decided to write another script from scratch, which might be easier to debug:
```
#!/bin/bash
cd ~/music
for i in *; do
  [[ -d "$i" ]] || continue
  for j in "$i"/*; do
    mv "$j" "$i-$(basename "$j")"
  done
done
```



Worked like a charm, thanks so much! Bonus points to have the script delete the original folders that are now empty after the mv.. :D

---

### Post by mssever on 2009-01-20
> **brdlvelixir said:**
> Bonus points to have the script delete the original folders that are now empty after the mv.. :D
```
for i in ~/music/*; do
  [ -d "$i" ] && rmdir "$i"
done
```This will delete all empty directories. If a directory still contains any contents, it will spit out an error message and skip it.

EDIT: Or, to modify the original script: ```

#!/bin/bash
cd ~/music
for i in *; do
  [[ -d "$i" ]] || continue
  for j in "$i"/*; do
    mv "$j" "$i-$(basename "$j")"
  done
  rmdir "$i"
done
```This will also spit out an error on a non-empty directory (the loop won't pick up dotfiles. To add them, change the inner loop to ```
for j in "$i"/* "$i"/.*; do
```

---

