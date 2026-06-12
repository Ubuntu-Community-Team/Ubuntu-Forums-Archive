---
title: "Protocols? Why?!"
date: 2009-05-07
forum: General Help
---

### Post by Xyem on 2009-05-07
Okay, this has actually irked me for quite a while and I was just wondering if anyone had any idea why they were implemented, possibly how to turn them off completely or to "fix" them.

Basically, things like the Trash, remotely mounted drives etc. are accessed through file managers ( Nautilus and Thunar ) with protocol addresses ( Trash:/// or SFTP:/// etc. ). This is all well and good *until you try to open a file*.

At which point, the program you have set to open that filetype ( GIMP for example ) goes "Trash:///file.jpg does not exist" because it doesn't understand the protocol. Why is this the default behaviour? It should be passing the *standard file path* seeing as other programs do not understand the protocol and they shouldn't have to! One of the strengths of the Linux filesystem is every file is under /. Period.

I'm not sure if this is specific to GNOME but the whole protocol thing just borks a lot of things up - completely unnecessarily. Do other desktop environments do this or is it GNOME specific? Can anyone recommend more sane file managers? Personally, I've resorted to just doing things on the command line.. but the other half isn't so inclined.

Thanks for listening to this rant :) Have a cookie.

---

### Post by theozzlives on 2009-05-07
If you were going to edit a file in Gimp, why would you put it in the Trash?

---

### Post by Xyem on 2009-05-08
Because <insert name of preferred image viewer> doesn't support XCF?

Besides, I get the same thing when I try to launch video files from a Samba/SFTP "mount" ( VLC doesn't understand smb://address/path/to/file but it would understand ~/.gvfs/address/path/to/file ) so your point misses my point.

Using protocols instead of file paths is a bad idea and it causes bugs like these: [https://bugs.launchpad.net/ubuntu/+source/gthumb/+bug/354401](https://bugs.launchpad.net/ubuntu/+source/gthumb/+bug/354401)

---

### Post by dandnsmith on 2009-05-08
This whole trash thing is something cobbled on, as is SAMBA, to support features found in Windows.
The thing to do, in lots of cases, is to extract or copy the file to a local place in the normal file hierarchy, and then you can operate on it.

Kludges necessitate more kludges to assist usage.

---

### Post by Xyem on 2009-05-08
That's the thing.. it *is* in the normal hierarchy ( under ~/.gvfs, except Trash ) but protocol paths are used ( passed as arguments to other programs etc. ) instead of the corresponding standard path, which causes completely unnecessary problems.

Also, copying it to the local filesystem might be undesirable if you are, for example, wanting to mount an 2G remote ISO..

---

### Post by detroit/zero on 2009-05-08
I've always found it to be annoying behavior, as well. An example I have ready at hand is: 

Say I delete a couple dozen photos from somewhere in my system, sending them to the Trash, but there's one I didn't want to delete, and so I go into Trash looking for it. None of the photos inside Trash have thumbnails, so it's not readily apparent which one I wanted to save, since all the images have names like "IMG_500.JPG" and "IMG_522.JPG".

Since the protocol is used instead of a regular file path, I can't even double click them to view them where they are - I have to select all of them, put them into a folder somewhere on the desktop or in ~, and then go through that folder trying to find the one picture I wanted.

(That leads to another fairly obvious question: It's the year 2009, and there no *Right-Click>Restore to Original Location* option in the Trash?)

I'd have to agree with OP. I'll go a little further and say that unless a certain thing has to do with network functionality or accessibility, protocol usage has absolutely no place inside a desktop operating system. Or, if you're going to write protocol usage into random pieces of your desktop OS, at least make sure the rest of the OS knows what those protocols are.

---

