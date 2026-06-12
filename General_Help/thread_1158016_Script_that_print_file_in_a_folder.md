---
title: "Script that print file in a folder"
date: 2009-05-13
forum: General Help
---

### Post by alek66 on 2009-05-13
Hi everyone I am trying to automate everything on my Ubunut Box that works as my server.

I created a shared folder where everybody drops their docs, txt, pdf and i wanted to know if there is a way to make a script that called with cron, print them every X hours, and them delete them.

Thanks!

---

### Post by mb_webguy on 2009-05-13
Sure.  The lpr command will print a file.  So all you would need to do is write a script that checks for files of specific printable mime types using "file --mime-type -b *filename*", prints them using lpr, and then deletes them.

You may want to consider moving the files to a different directory temporarily rather than deleting them.  You could have the script run once a day, delete the files from the temporary directory, print the files in the main directory, then move them to the temporary directory.  This would give you a day to make sure that the files printed correctly and try to print them again if they didn't.

---

### Post by HermanAB on 2009-05-13
Howdy,

See this:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

---

### Post by alek66 on 2009-05-14
Thanks a lot to both. Its better to move them to  temporary dir, mostly are .docs or pdf files.
I thougt to make a script that look the whole dir prints them moves them. Using cron to call it every 5 hours.

Thanks for the help!

---

### Post by alek66 on 2009-10-10
I got my script----but I cant get it to run,
heres my script.sh
```
#!/bin/sh

for filename in `ls $Dir'
do

	if [ -s $filename ]
		then

		echo 'do you want to print $filename ?"
		read answer

		if [ "$answer" = y ]
			then
			lpr -H localhost $filename
			mv  $Dir/$filename $Dir/Printed/$filename.old

		fi
	fi

done
```
The asking if I want to print, if check debuggin porpouses.
When i sh Script.sh I get this Script.sh: 19: Syntax error: EOF in backquote substitution

What am I doing wrong here..

---

### Post by alek66 on 2009-10-30
bump...

---

