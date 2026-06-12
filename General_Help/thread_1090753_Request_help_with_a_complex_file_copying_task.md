---
title: "Request help with a complex file copying task"
date: 2009-03-08
forum: General Help
---

### Post by Mainiak Blaniak on 2009-03-08
Hi Folks,

My goal is to find a way to copy album cover art from directories on my PC running Ubuntu 8.04 to a Sandisk Sansa running rockbox.  I use Amarok to manage my music on the PC and was hoping for a nice way to make Amarok do what I want, but haven't been able to find a way.  What I'm looking for is a way to copy album art files from the PC to the Sansa.  

the album art files are all cover.bmp files stored in the corresponding album file on the PC.  Both the PC and the Sansa use the same /artist/album directory structure.  My problem is that I don't know how to limit the copy of album art from the PC only to the existing subset of the file structure on the media player.

As of now I'm able to copy the entire file structure from the PC to the Sansa to put ALL of my album art on there, but this is very in-elegant and results in about 4x as much album art on the player as there is actually music there that uses it.  

Is there a command to read the file structure on the player, and then find and copy album arts from the corresponding file structure on the PC without copying/creating files that weren't on the player to begin with?

Thanks in advance and hope this isn't totally confusing...

Mainiak Blaniak

---

### Post by heindsight on 2009-03-08
Well assuming your media player is mounted at /media/Sansa with your music under /media/Sansa/Music, and the music on your PC is in /home/yourusername/Music, you could do something like:

```
find /media/Sansa/Music -maxdepth 2 -mindepth 2 -type d -printf "%P\n" | while read album; do
  if [ -e "/media/Sansa/Music/$album/cover.bmp" ]; then
    continue
  elif [ -r "$HOME/Music/$album/cover.bmp" ]; then
    cp "$HOME/Music/$album/cover.bmp" "/media/Sansa/Music/$album"
  fi
done

```
You may have to tweak this a little to suit your needs,

Have a look at the find manual for details on how it works and what options are available:
```
man find
```

---

### Post by Mainiak Blaniak on 2009-03-08
Wow,

Thanks a bunch Heindsight!  I'll be giving this a try shortly.  I'm VERY new to shell commands...once i see something I can pretty much understand what is doing what, but I'm not to the point of working out the syntax myself yet.  

this will take very little tweaking to make my directories line up.

Appreciate the quick response!:)

MB

---

