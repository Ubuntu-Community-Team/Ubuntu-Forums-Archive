---
title: "Album cover images cause Rhythmbox to crash, how can I filter them out?"
date: 2005-02-06
forum: Desktop Environments
---

### Post by thorN on 2005-02-06
When I try to import the music folder into Music Player, it crashes after a while: I think this is becuase it's trying to load image files as music.

Is there a way I can filter these out so I can use the music library?

All our music files are stored on a Windows XP file server, with folders for each artist/album. I don't know how to use "search for files..." to search network locations, and I can't just sort by file type because the files are all in subfolders- is there a way I can view all files in subfolders?

Thanks for any help you can offer.

---

### Post by valadil on 2005-02-06
It's not the album art that causes this so much as the desktop.ini files that make the art into the wallpaper of the album folder under windows.  At least I think so.  Since my music is stored locally I did some scripting to delete all the album art.  That's not a particularly good solution for you though, since it's shared...

If you add mp3 files individually rhythmbox should be okay.  You can also make a script to generate rhythmdb.xml.  I wouldn't be surprised if such a script is already out there.  If you'd rather do it yourself, just clear rhythmbox's library and load one or two songs in there for reference.  I think rhythmdb.xml lives in .gnome2/rhythmbox/ though I could be wrong.

---

### Post by thorN on 2005-02-06
[QUOTE=valadil]It's not the album art that causes this so much as the desktop.ini files that make the art into the wallpaper of the album folder under windows.  At least I think so.  Since my music is stored locally I did some scripting to delete all the album art.  That's not a particularly good solution for you though, since it's shared...

If you add mp3 files individually rhythmbox should be okay.  You can also make a script to generate rhythmdb.xml.  I wouldn't be surprised if such a script is already out there.  If you'd rather do it yourself, just clear rhythmbox's library and load one or two songs in there for reference.  I think rhythmdb.xml lives in .gnome2/rhythmbox/ though I could be wrong.[/QUOTE]
 Ah yes, there's thumbs.db files in the folders with cover images. I wouldn't mind removing the cover art/thumbs.db files, since they're rarely used anyway.

I'm new to Linux, so I'm not sure what you mean by 'scripting' (and the only scripting language I know is PHP).

I wouldn't really want to add each folder individually, there's absolutely loads of them.

It seems the easiest way would be to find *.jpg and *.db and delete them: but I don't know how to do this either :)

You were right, the songs/internet radio stations are stored in rhythmdb.xml. Ideally I'd have a program to scan the music share and generate an XML file periodically.

---

### Post by valadil on 2005-02-06
Before you start with this script you should note that I remove a fairly large list of files from a music directory.  If you do mot feel comfortable with this, feel free (or even encouraged since I don't want to be blamed for loss of music) to change rm to mv and add a target dir.  Then it'll just toss all the albumart to the new folder but you can scan that for mp3s yourself, just in case you don't want to lose music.

--

locate /mnt/music | grep jpg
Assuming /mnt/music is where the music lives, this will give you all the jpg files in your music folder.  

I would say to rm the list of jpgs, but it'll get confused when spaces get involved.

So let's put that whole list into a text file:
locate /mnt/music | grep jpg > jpglist.txt

(Note that there are other, probably better ways of scripting this, but this is the first way that popped into my head.)

Count how many lines of files there are to remove in your jpglist.txt
wc -l list.txt

I get 73 jpgs that have found their way into my music folder since the last time I purged them.  


Now we start a for loop.  Since you said you know PHP I don't have to explain what a for loop is.

for i in `seq 73` ; do rm "`cat jpglist.txt | head -n $i | tail -n 1`" ; done

The head/tail stuff just finds the ith line in a file by returning the top i lines and then giving you only the last 1 line out of those.

One other note is to make sure you run updatedb before doing all this, as locate is dependant on that.

---

### Post by thorN on 2005-02-06
Sorry if I'm fustratingly slow, but I don't know how to do scripting at all. (Is it a part of Gnome?)

I've learned from the Rhythmbox mailing list that version 0.9 will support album covers (and download them off amazon). I'll wait until then I think.

And also, how do I go about mounting a network place into a path in /mnt/?

---

### Post by valadil on 2005-02-06
Scripting is generally done in a terminal.  You just type in the commands and watch them go.

Glad to hear rhythmbox is gonna be adding that.  It's been a problem for quite some time now.

Mounting network shares depends on how they are being shared.  Windows file sharing is controlled via samba.  To mount a samba share you do something like this:
smbmount //server/share /mnt/mount_point

And the contents of /mnt/mount_point will be whatever server is sharing in the folder share.  NFS mounting is similar:
mount -t nfs ip.of.server:/path/to/music/files /mnt/mount_point

---

### Post by h4d on 2005-02-06
By the way, ryhtmbox 0.8.8 already imports a folder which contains jpgs...I'm using it in Hoary flawlessly. On the other hand, xmms is broken in hoary :(

---

