---
title: "Major copy&amp;paste weirdness"
date: 2006-06-22
forum: Desktop Environments
---

### Post by ajifans on 2006-06-22
Experiencing some majorly weird issues when copying and pasting to my iriver ihp120 (mp3 HD player).

I copied and pasted (right-click copy source, left-click paste destination)some folders of MP3's onto the ihp120 drive (as I'd always previously done fine with both XP and Suse (KDE)).

Everything seemed fine; I could see them and I could play them.  However upon playing the full tracks I became aware that the mp3's had become spliced with other MP3s.

E.g. Each track of Serena Meneesh's (Norwegian indie/post-rock) album was spliced with a track from Herbie Hancock's 'Futureshock'!!  I.e it starts with the one and ends with the other.
Other example, listening to Current 93 tracks which suddently turn into Daft Punk tracks (and the changeover from Neo-folk to dance is very noticeable!!).

It's weird enough as it is, but;
 -- The source files on my desktop are intact.
 -- I don't have any Herbie Hancock on my ihp 120, only in a directory on my computer that was different from the one I copied and pasted from.
 -- The track lengths are still the same (I think).

Anyone have possibly any idea how this could happen?  
Usually if I have a problem, can think of a good reason or know of sensible questions to ask, but this seems really mental!

---

### Post by pellgarlic on 2006-06-22
hey, that _is_ weird!!!

the only thing that *i* can think of, is that either (a) you are using lvm, and something has gone funny with that, or you (b) are using a journalling file-system, and something has gone funny with *that*.

applause, please, for my comprehensive and exhaustive answer! :)

seriously though, is either of my guesses right?

also - are the files that are splicing together named the same? i.e. - are the tracks just called "track 1" or something generic like that, or are they named according to the song titles etc?

---

### Post by ajifans on 2006-06-22
The track names are completely different.

I'm copying from my home partition, which is ext3 to my mp3 player which is FAT32.

Not sure about lvm. (Don't really understand it to be honest).

When I copy just 1 folder it seems file, it's just when I copy a bunch of folders that mad stuff happens.*

Might try installing KDE, to see if it's specific to gnome.

---

### Post by pellgarlic on 2006-06-22
you could try this:

open a terminal, and type

```
cp -R /home/ajifans/folder-you-want-to-copy /media/whatever-your-mp3=player-is-mounted-as
```

(assuming your login name is "ajifans". if not, replace that with whatever it is :)

this method should bypass the desktop manager (gnome) altogether, and will copy whatever folder you dictate in the first field, plus everything that's inside it (that's what the "-R" does)

if that works, that narrows down the list of potential problems.

[Edit: 

the above will only help if you select a folder to copy that has other folders in it - to select multiple folders individually, just list them in a row - the last location in the line will be taken as the destination, so you could do:

```
cp -R /home/ajifans/music/Sereenah-Meneesh /home/ajifans/music/Current-93 /media/mp3-player
```

for example. the "-R" is reuired to copy the contents of a folder, be it other folders, or the files it contains]

---

### Post by ajifans on 2006-06-22
Thanks for your help.  I was thinking of trying that, but I don't know how to copy multiple folders at the same level (i.e. not subdirectories) from the command line (CLI equivalent of ctrl-clicking a number of folders and then copying/pasting).

One at a time is okay.

Not sure if it is relevant but a related problem I'm having (and reason I'm bothering to right-click and then copy/paste) is that when I just drag the folders from the desktop to the media player it copies blank versions of the files in question to the mp3 player - e.g. songname.mp3 with 0 bytes.

When I deleted these files it created a hidden folder (.Trashes-username), and within this folder were the deleted files and a directory.  Within the that folder was the same files and directory, which in turn had the same files and the directory.  This appeared infinite.  I couldn't delete this directory, nor its subdirectories.  It took up no space, but my MP3 player thought it had 99999 files and 9999 folders and consequently took 30 mins to boot up and down as it got seriously confused.  I ended up with the nuclear option of reformatting the drive.

(on the bright-side if worse comes to the worse I'll get some CLI practice :-D )

---

### Post by pellgarlic on 2006-06-22
when you tried to delete the directory, did it say "you do not have permission" or something like that? if so, it would have required root permissions, so a "sudo rm /media/mp3-player/.Trash-username" would be required in order to delete it. also, in natuilus options, there is a setting to include a "delete directly" option in the right-click context menu, which bypasses the trash. this is good for small capacity removabel usb drives, which get filled quickly if you don't remember to empty the trash every so often :)

---

### Post by ajifans on 2006-06-22
I guess it must be a weird gnome <-> iriver thingy.

Good old CLI worked a treat.

Would like to know how to stop it happening though.  I guess it's probably too weird even for experienced users.

---

