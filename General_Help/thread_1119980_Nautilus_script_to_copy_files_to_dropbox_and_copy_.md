---
title: "Nautilus script to copy file/s to dropbox and copy public URL."
date: 2009-04-08
forum: General Help
---

### Post by RyconPayne on 2009-04-08
This is functionality this program is screaming for.  The ability to right click a file, or multiple file, send them to dropbox, and copy the public URL of the file or files you copied.  

They have a python script for this for windows: [http://forums.getdropbox.com/topic.php?id=4403](http://forums.getdropbox.com/topic.php?id=4403)

I am not good with scripting yet, it's something I'd like to learn eventually.  I have found a Nautilus "Copy To..." script on the UbuntuForums, and learned that xclip is the command I'd need to use.  Beyond that, I'm lost. 

Here is the nautilus script in I found: [http://ubuntuforums.org/showthread.php?t=417978&highlight=nautilus+actions](http://ubuntuforums.org/showthread.php?t=417978&highlight=nautilus+actions)

If someone could shed some light on this, and make this functionality actually work for me, I'm sure I'm not the only one that would appreciate this.

Thanks.

---

### Post by RyconPayne on 2009-04-09
I figured it out.  I'm sure it's not the best way to do this, but through trial and error, this is what I figured out.  If anyone has any cleaner ways to do this, I'd be happy to learn more.

Copy Single file to Dropbox and copy public URL:
(first shell script ever)
```
#!/bin/bash
cp $1/$2 /home/rycon/Dropbox/Public
text="http://dl.getdropbox.com/u/*******/$2"
echo -n "$text" | xsel -ib  ## xclip -i -f -selection "clipboard"
```
I was figuring out which I'd rather use, xclip or xsel. I obviously decided on xsel.

Copy Multiple files to Dropbox and copy public URL:
(upgrading the first script)
```
#!/bin/bash

#  Copy files to Dropbox and create file with Public URL for files
(while [ $# -gt 0 ]; do
	cp $1 /home/rycon/Dropbox/Public	
	echo "http://dl.getdropbox.com/u/*****/$1" >> /home/rycon/temp/dropbox
	shift
	done
)

#  Remove blank line at the top of output file.
mv /home/rycon/temp/dropbox /home/rycon/temp/dropbox.tmp
sed 1d /home/rycon/temp/dropbox.tmp > /home/rycon/temp/dropbox
rm /home/rycon/temp/dropbox.tmp

#  Copy contents of file with URLs to the clipboard.

cat /home/rycon/temp/dropbox | xsel -ib  ## xclip -i -f -selection "clipboard"
```

---

