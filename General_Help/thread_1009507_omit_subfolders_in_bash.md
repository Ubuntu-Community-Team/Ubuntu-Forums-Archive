---
title: "omit subfolders in bash?"
date: 2008-12-12
forum: General Help
---

### Post by theevilhamster on 2008-12-12
Hi,

i want to tar a folder, but do not want to tar some of its subfolders.
e.g. i want to tar my home directory, but not the videos directory within it.

can i do this with a bash command or do i have to manually list all of the other subfolders?
would be a great help, and will save a lot of effort.

thanks

---

### Post by cb34 on 2008-12-12
do you use a gui at all, cuz it would be pretty easy that way selecting everything to add to the archive except the certain dir you don't want.

or.. there may be a way to do it by changing the permission of the dirs you dont want.. or maybe.. there is a combo of options you can use with tar.. theres tons of options for tar.. did a search on google: tar first link looks very useful if you didn't already see that info. im also thinkin of a script that would tar the first dir on the list how you want, then print a list of the dir structure to a file and have it go down line by line with an argument looking for the dir names you dont want, and have it skip that line and continue on.. so a script that would list the dir scructure to a file, read that file goin down the list ine by line until it finds a line you specified you dont want, and skip that.. and keep appending to the tar file you're making..

somethin like that.. just a brainfart.. not that i could easily or quickly write that up.. im not that good.. yet.. but for anyone that's good with scripting.. this should be.. iMO.. very simple.  im just good at the brainfart part. :D

good luck.

---

### Post by cb34 on 2008-12-12
do you use a gui at all, cuz it would be pretty easy that way selecting everything to add to the archive except the certain dir you don't want.

or.. there may be a way to do it by changing the permission of the dirs you dont want.. or maybe.. there is a combo of options you can use with tar.. theres tons of options for tar.. did a search on google: tar first link looks very useful if you didn't already see that info. im also thinkin of a script that would tar the first dir on the list how you want, then print a list of the dir structure to a file and have it go down line by line with an argument looking for the dir names you dont want, and have it skip that line and continue on.. so a script that would list the dir scructure to a file, read that file goin down the list ine by line until it finds a line you specified you dont want, and skip that.. and keep appending to the tar file you're making..

somethin like that.. just a brainfart.. not that i could easily or quickly write that up.. im not that good.. yet.. but for anyone that's good with scripting.. this should be.. iMO.. very simple. im just good at the brainfart part. :D

good luck.

---

### Post by dagnabit dang doohickey on 2008-12-12
[tar --exclude=PATTERN]("http://unixhelp.ed.ac.uk/CGI/man-cgi?tar")

---

### Post by cb34 on 2008-12-12
haha yup.. was just tryin to write a script to do this then found the tar commands to do it.. nice one dagnabit dang doohickey..(nice name:))

tar -cvf ArchiveName DirToTar --exclude "write the full path of the dir u dont want to tar in these quotes"

and to exclude more than 1 dir, you need to write --exclude again and the next dir path you want to exclude, and again and again if you have more to exclude.
---

if you have many dirs to exclude, you can put them in a file, and have tar read that file to know what to exclude.

doing:
tar -cvfX ArchiveName ExcludeFile DirToTar

peace.

EDIT-> theres also a guy out on the net that says he had problems with the syntax of the first command, instead of doing:
tar -cvf ArchiveName DirToTar --exclude "/blah/blah/blah"

what worked for him was:
tar -cvf ArchiveName --exclude "/blah/blah/blah" DirToTar

switched up the syntax and it worked for him.. differences between Tar and GNU Tar he says.
thought it was worth puttin it here.

overNout

---

### Post by theevilhamster on 2008-12-15
thanks a lot guys:). will include this in my backups in crontab. can I do this also with other commands like cp/mv?

---

