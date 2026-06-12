---
title: "Help with cp command to recursively copy with wildcard"
date: 2009-05-25
forum: General Help
---

### Post by BandD on 2009-05-25
I'm trying to copy some images from one icon theme to another.  But I only want a the speaker icons that display the volume level. They are all stored within icon-set-a in folders 22x22, 24x24, 36x36, 48x48 etc.  Within each of those folders they are within the status folder and all start witht he word audio.

The file structure for the 22x22 folder for audio-volume-high icon looks like this:

/home/bandd/.icons/set-a/22x22/status/audio-volume-high.png (so you can replace 22x22, with 24x24, 36x36 etc).

I'm comfortable with the command line, but I don't have a lot of practice with wildcards and how to construct a command that will let me recursively copy all of these images named audio-*.png within all of these different folders.

Is there a way to do this sort of thing with the cp command?

Thanks!

---

### Post by BandD on 2009-05-25
I just relaized that I'd have to have a command that took the files from the /set-a/22x22/ folder and put them in /set-b/22x22/ folder.  So it'd probably have to be more of a script.  But I'm still curious how you could selectively copy items like the above description via the command line. (i.e. I want all the copy the files mentioned above into their own new directory say /home/bandd/test).

---

### Post by unutbu on 2009-05-25
The command
```
rsync -avm --include='audio*' -f 'hide,! */' /home/bandd/.icons/set-a/ /home/bandd/.icons/set-b/

```
will copy any file of the form "audio*" in any subdirectory of /home/bandd/.icons/set-a/
and copy it to the corresponding location in /home/bandd/.icons/set-b/.

An explanation of the command can be found here:
[http://ubuntuforums.org/showpost.php?p=6010205&postcount=15](http://ubuntuforums.org/showpost.php?p=6010205&postcount=15)

---

