---
title: "How can I edit tags in AAC/m4a files?"
date: 2005-12-11
forum: General Help
---

### Post by eduardgrebe on 2005-12-11
I have installed the restricted format gstreamer plugins and can play my iTunes generated AAC music fine in Rhythmbox. However, I have a problem with multi-disc albums, since Rhythmbox doesn't seem to read the "Disc x of x" tags. To solve this I need to edit the tags in my m4a files, but neither Rhythmbox nor any of the ID3 tag editors I have found can do this. 

Does anyone know how I can edit my m4a tags?

---

### Post by MetalMusicAddict on 2005-12-11
I dont have any AAC/m4a files but [EasyTag]("http://easytag.sourceforge.net/") will do it. Its in the repos.

---

### Post by eduardgrebe on 2005-12-12
I tried EasyTag, Audio Tag Tool and Ex Falso, none of them seem to work.

---

### Post by signbarn on 2005-12-12
Yeah, this has me stumped also. I now use the SVN version of amaroK. it lets me edit them in my collection, but I'm not so sure whether it actually edits the tag, or if it just edits a table in its internal database.

Either way, I'm satisfied -- even though installing amaroK SVN on Ubuntu (GNOME) requires i install *many* otherwise useless KDE libraries.

---

### Post by Bazon on 2006-04-22
*gtkpod aac* can tag m4a/aac files. Anyway I don't like that as I can't call it with an argument.
*(I like to rightclick the folder and call the tag-editor with nautilus-actions which works for easytag...)*

I would prefer to be able to use easytag for m4a. :(

---

### Post by mazirian on 2006-07-24
How annoying.  easytag worked fine for this purpose in Gentoo.  The package in the ubuntu repository must be built without aac support.

---

### Post by foolishchild on 2006-10-22
I have discovered that exfalso can edit tags in m4a files, though it is not a command line tool - you have to use the gui. This despite the fact that the ubuntu version of quodlibet (which exfalso seems to be a part of) does not find m4a files - it finds mp3 (and presumably ogg vorbis).

So.... I really like the version of amarok which can now add m4a files to it's collection of music, play them, synch with an ipod etc. But to edit tags, I have had to install exfalso, which comes with quodlibet, which can't handle m4a files.

Hope this helps somebody.

---

### Post by sinaen on 2006-10-23
have you tried with m4b files?

---

### Post by mazirian on 2006-10-23
Easytag may be built with the necessary support for editing m4a files. There is a howto elsewhere in the forums.  Failing the adventurous compiling spirit, there are also debs floating around on the forums for an easytag-aac that will do the trick.  Should work with m4b files as well.

---

### Post by sinaen on 2007-10-09
Easytag Does NOT support m4b files at all.. :/ maybe i do have one thats not supporting aac/m4a/b files

and Amarok can't acess them at all to write to the database

GtkPod can change in its own database but does nothing to the tags in them selfves

so its a real bugger

sincerely wanting an program to edit tags to my audioboks etc..

---

### Post by musicinmybrain on 2007-12-30
As foolishchild said, Ex Falso seems to be the only thing out there at the moment that can do it.

---

