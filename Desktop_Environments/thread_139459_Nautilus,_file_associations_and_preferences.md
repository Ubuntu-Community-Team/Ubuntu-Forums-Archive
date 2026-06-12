---
title: "Nautilus, file associations and preferences"
date: 2006-03-04
forum: Desktop Environments
---

### Post by engine on 2006-03-04
I have a stack of text files for the mup score-publishing program, all with .mup as extension so I can transfer them to other systems. I Open a directory in Nautilus 2.12.1, and see that some of them are identified [Type column] as 'mup document' with MIME type application/x-extension-mup and others as 'plain text document' with MIME type text/plain. I can't see anything different in the file properties or even the first few lines. 

Better yet, when I right-click to check the properties, Nautilus almost always changes the 'mup document' files to 'plain text'.

The on-line help says I should use "the Edit file type dialog in the File Types and Programs preference tool". I'd love to, if I could find the preference tool <vbg>

Hints on where to find this tool - or any other reliable way to set the MIME type for files on the basis of extension or header - welcome!

---

### Post by Madpilot on 2006-03-04
Right-click on a .mup file, select Properties -> Open With tab.

You might have to add mup to the list of apps there.

Note that this might not be flawless - there are bugs in Gnome's MIME-type tools that I've run into...

---

### Post by engine on 2006-03-05
Thanks for your reply, but perhaps my posting was too wordy - I don't want to open files with mup, I want to associate a mime-type with mup files. Right-click on properties shows me the mime-type "the system" has arbitrarily associated with the file, but doesn't let me set the mime-type. The tool the Helps say _will_ let me do that doesn't seem to exist.

---

### Post by Gee on 2006-03-17
right click on a file with whatever extention you want to associate
> properties
> open with

select the one you want to use

it was confusing the hell out of me too :)

---

### Post by engine on 2006-03-19
Properties > open with is fine for one file at a time, but doesn't get any farther towards setting up an association for all files with the same extension.

---

### Post by kevinlyfellow on 2006-05-17
[http://freedesktop.org/wiki/Standards/AddingMIMETutor]("http://freedesktop.org/wiki/Standards/AddingMIMETutor")

Although, I can't seem to get this to work... gnome really needs to work on the way it handles mime type

also

[http://weblog.zerokspot.com/posts/35/](http://weblog.zerokspot.com/posts/35/)

and 

[http://ubuntuforums.org/showthread.php?t=129154](http://ubuntuforums.org/showthread.php?t=129154)

---

