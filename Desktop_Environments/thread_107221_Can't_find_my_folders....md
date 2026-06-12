---
title: "Can't find my folders..."
date: 2005-12-22
forum: Desktop Environments
---

### Post by Cless on 2005-12-22
Some of my folders and files are unseeable when I try to access them through GUI. It's not many though. All of the folders contains music files (mp3). The folders aren't hidden or anything...

Do you know what's wrong?

Edit: [Picture]("http://img321.imageshack.us/img321/7632/screenshot2nc.png")

---

### Post by Cless on 2005-12-22
Double Post... Sorry.

---

### Post by Sheco on 2005-12-22
have you tried renaming the folder maybe? or moving it somewhere else?

---

### Post by daschl on 2005-12-22
well that really sounds strange.

maybe it helps if you refresh the browser (by klicking on the foldername again?)

that is really annoying becaus it isnt a dotfile or something like this.

do you can view it with other methods of file-browsing? (just open firefox and go to open file -> and select view all files)

or is the only way to access the folder via shell?

really confusing...

---

### Post by Cless on 2005-12-22
Thanks for the answer, Sheco and daschl! 

It worked when I renamed the folder. It seems like the nautilus doesn't support the "~"-sign. That sucks =(

---

### Post by steve.horsley on 2005-12-22
[QUOTE=Cless]Thanks for the answer, Sheco and daschl! 

It worked when I renamed the folder. It seems like the nautilus doesn't support the "~"-sign. That sucks =([/QUOTE]

Yes - it seems to be a bug in Nautilus - it doesn't show files or folders ending in '~'. 

It does show files and folders starting in '$sys$' though.

---

### Post by daschl on 2006-01-11
[QUOTE=steve.horsley]Yes - it seems to be a bug in Nautilus - it doesn't show files or folders ending in '~'. 

It does show files and folders starting in '$sys$' though.[/QUOTE]

in the options you find something like "show hidden files and backups" or stuff like this (i dont know exactly because i use the german version)

check this and it works :)

edit:
duh, it doesn't work either

---

### Post by Gustav on 2006-01-11
Files ending with ~ are (believed to be) backups (just as files beginning with . are hidden) and made invisible in nautilus (if you don't check the "show hidden" option).

---

