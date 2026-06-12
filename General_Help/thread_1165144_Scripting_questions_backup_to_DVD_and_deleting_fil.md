---
title: "Scripting questions: backup to DVD and deleting files"
date: 2009-05-20
forum: General Help
---

### Post by dh003i on 2009-05-20
Hi all,

I'd like to create two scripts in bash...how can I do this:

**First Script: Deleting .ORF Files**

I have .ORF and .JPEG files, each with the same name before extension (i.e., _15355.ORF and _15355.JPEG). I've deleted .JPEG files I don't want, and want to make a script to get rid of the corresponding .ORF files. I.e., I want to make a script that will, within a folder, find all .ORF files that don't have a corresponding .JPEG file and delete them.

**Second Script: Backing up to DVD simply, without splitting files, and restoring**

I want to create a script that will backup all files in my /home/user folder to a DVD, but without compressing or archiving them. All of my files are already compressed (i.e., jpeg, mp3, flac, or documents), and I doubt there will be significant gains from compression. Also, I want to be able to easily browse these backup DVDs on any computer without untarring ungzipping them. 

So how do I make a script that will:

1. Backup all files in /home/user to a DVD
2. Eject the DVD
3. Prompt the user to label the DVD with the folders that have been placed there (and for the last folder, of which the contents would likely be split, to write the last file in that folder that's on the DVD).
4. Make a database of the contents of the DVDs and number each DVD starting from 1
5. Ask for the next DVD to continue the backup
6. Restore the files (selectively if necessary)

(or a program that can do this)

---

