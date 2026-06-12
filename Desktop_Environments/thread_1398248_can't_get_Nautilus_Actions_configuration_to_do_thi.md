---
title: "can't get Nautilus Actions configuration to do this"
date: 2010-02-04
forum: Desktop Environments
---

### Post by ray field on 2010-02-04
I'd like to be able to copy the contents of files to the clipboard by clicking on them in Nautilus, by using a batch routine with xclip.  I think I am close to being able to do this in Nautilus, but for some reason it's not working.

I've got a few dozen text files in a directory, all with the extension "clipz," viz.

MyFavoriteUrl.clipz

I know I can use xclip to copy the file contents to the clipboard thus:

```
xclip -i -selection c MyFavoriteUrl.clipz
```

but I can't seem to get this working in Nautilus Actions Configuration.	 here's what I've tried:

1) add item "xclipper"
2) 	label: xclipper
	tooltip: Copy file contents to clipboard
			
3) Edit profile "Main":
	path: /usr/bin/xclip
	parameters: -i -selection c %f

	under conditions: Filenames: 	*.clipz

I've jiggered and re-jiggered every which way, & still cannot invoke the right-button selection of xclipper to successfully copy the file contents to the clipboard, even though the command-line use, as above, works just fine.

ideas?

---

### Post by ray field on 2010-02-05
[ bump ]

---

### Post by ray field on 2010-02-06
a look at the faq for N.A.C.

[http://www.grumz.net/index.php?q=node/7#q1](http://www.grumz.net/index.php?q=node/7#q1)

shows that %f specifies only the filename (& assumes it's from the home directory) -- %M specifies full pathname/file

---

