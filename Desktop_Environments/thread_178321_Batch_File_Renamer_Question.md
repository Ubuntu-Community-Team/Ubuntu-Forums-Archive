---
title: "Batch File Renamer Question"
date: 2006-05-17
forum: Desktop Environments
---

### Post by Admiral Valdemar on 2006-05-17
I'm in the process of re-ripping my CD collection to Ogg Vorbis standard (just got a new digital audio player that doesn't support AAC, but does support Ogg), but what bugs me is that I have the MP4 files there with their names as I want them, but not on the new ripped files. How can I copy the filenames from the MP4 files to the new Ogg ones, or isn't there anything that can batch copy filenames that way?

I considered KRename, but it won't let me put in one set of files and copy their names to another set of files like I want.

---

### Post by stealth_gsx1300r on 2006-05-17
You have kind of tricky problem.  Typically if you were transcoding the file from one file format to another you could use a batch script.  For example.

for i in *.mp3; do lame --decode "$i" `echo $i | sed 's/.mp3/.wav'`; done

this command for example, would work if you were changing mp3's back into wav files.  It really depends on how you are doing it.  If you are ripping from CD's, then you should be able to use the name of the track pulled from CDDB or the sort.  If you are batch transcoding through a script, you should be able to do something like the command above to get the desired result.  Also, if your oggs have i3d tags, you can use tools like tagtool to use the embedded id3 tags to rename the songs.

---

