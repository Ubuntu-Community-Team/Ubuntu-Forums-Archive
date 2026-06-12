---
title: "Could this be a virus?"
date: 2010-08-03
forum: Desktop Environments
---

### Post by nsharish on 2010-08-03
I am using Ubuntu Karmic. I noticed weird behaviour in file/folder icons today.

1) Some of file and folder icons became bigger/smaller in size.
Some had an icon embedded on them. The icon resembles that of tomboy notes. The `notes` tab for those unusual file/folder properties had `F#` text. When I rename such a  folder/file it gets back to normal size. But when renamed back again, it becomes smaller/bigger again.

2) Nautilus could not open some of those folders(not all). Nautilus simply exits without showing any error messages when opening those folders.

3) When I logged in today, my desktop icons where shockingly big(Each icon about half the screen size). I selected all and chose `restore icon's original size`, which brought them to normal size. I could not reproduce this behaviour and so I could not get a screenshot of it.

I have added some screenshots.

I don't use root and I don't remember doing any package upgrades recently.

Could this be a bug or an unwanted program causing problems?. Anyone had this problem before?.

---

### Post by ronnielsen1 on 2010-08-03
You would be the first one to get a virus. Nautilus is not going to be able to open up some of these. Some of them are text files which would require a text editor like gedit.

> Vimperator is a free browser add-on for Firefox, which makes it look and behave like the Vim text editor.
[https://addons.mozilla.org/en-US/firefox/addon/4891/](https://addons.mozilla.org/en-US/firefox/addon/4891/)
> Vim is a highly configurable text editor built to enable efficient text editing. It is an improved version of the vi editor distributed with most UNIX systems.
[http://www.vim.org/](http://www.vim.org/)
> [Apvlv]("http://code.google.com/p/apvlv/") is a  nifty PDF document viewer. With Apvlv, you can read PDF documents like using Vim. For Vim fans, that’s quite cool. 
[http://lazyubuntu.com/view-pdf-documents-with-apvlv-on-ubuntu.html](http://lazyubuntu.com/view-pdf-documents-with-apvlv-on-ubuntu.html)
> **.vimrc and customization**

   vim is extremely customizable. It will read the file .vimrc  in your home directory before it starts. This file can contain settings  and even scripts. The below settings are ones I've found helpful -- give  them a try!

[http://jmcpherson.org/vimrc.html](http://jmcpherson.org/vimrc.html)
Looks like they're all related to vim. Why your graphics had a hiccup, I fon't know but it's not a virus

---

### Post by nsharish on 2010-08-03
The screenshots posted were just samples from my home folder. There are many such files and folders existing at random places in subfolders too. 
All screenshots relating to vim was just coincidental.

I am still not able to open those folders in Nautilus. I could only use terminal to access those folders. Please help me with this.

---

### Post by phildini on 2010-08-03
Are you sure the permissions are correct on these files? Since you can access them via command line, what is the output of ```
ls -lah
``` on those files?

Additionally, have you made any major system changes recently?

---

### Post by nsharish on 2010-08-04
`-rwxr-xr-x 1 harishanandns harishanandns 25 2010-02-14 23:24 gtkrc-2.0`

This is what is returned by *`ls -lah`*. Those files were not present in specific folders, they were present here and there. All the files returned same output as above. 

One more thing I noticed was I could open the subfolders of those unusual folders in nautilus thro terminal. 

I do upgrade some software packs (firefox,etc). I did not do any major changes/upgrades.

I am unable to figure out?

---

