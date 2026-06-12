---
title: "Using terminal to find al files of a certain type, and move them all to one folder"
date: 2009-03-30
forum: General Help
---

### Post by scratman on 2009-03-30
I have copied all of my music, videos and documents from three old hard drives to my new external.  The thing is, I now have loads of duplicated files which I do not need.  I simply created folders called OldHDD1, OldHDD2, OldHDD3 and moved all of the folders I wanted to keep to them.  I have also created folders for music, video, pictures etc.  Ideally what I would like to do is move my files from the OldHDD folders to the relevant folders by file type.

I know that I can do a ```
find -name "*.filetype"
``` to locate the relevant files, and if I add ```
>> filetype.txt
```, it will output the locations of all the files of the specified type to a text file for me.

Ideally, I'd like to be able to search my external hard drive for all mp3 files an move them to my new mp3 folder, and overwrite any duplicate files.

Does anybody know how I could do this in Terminal?

Many thanks in advance.

---

### Post by aeiah on 2009-03-30
find /path/to/folder -name *.mp3 -exec cp {} /path/to/copy/to \;

i havent tested it. i just grabbed it from google because im not on a linux box right now. it'll copy rather than move so you can just delete what it creates if it doesnt go smoothly. you'll probably want to add an argument to cp so it overwrites without asking

---

