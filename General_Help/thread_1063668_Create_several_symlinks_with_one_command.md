---
title: "Create several symlinks with one command"
date: 2009-02-08
forum: General Help
---

### Post by jonasback on 2009-02-08
Hello everyone!

I'd like som help with creating symlinks. My setup is something like this.

/media/storage/all/movies  <-- i wan't symlinks to all movies into this folder


/media/storage/packs/pack.nr.1/
movie1
movie2
movie3

/media/storage/packs/pack.nr.2/
movie1.1
movie2.1
movie3.1

and so on..

In some of the packs I have about 40 subfolders and want to symlink all folders at the same time. Any possible solutions?

Thx!

---

### Post by Ng Oon-Ee on 2009-02-08
A simple bash script which does the following (in pseudo-code)...

INPUT - some folder
1. Check if its a folder, if yes, go to 2, if not, go to 3
2. Recursively run itself on every folder/file within the folder
3. Check if the file is a movie, if yes go, go to 4, if not, go to 5
4. ln -s <input_file_path> <output_file_path> (you can use some simple renaming here, especially if the movie files are likely to have the same file-name)
5. Do nothing.

Sorry, my bash-scripting is mainly copy-from-example based, so I'd hesitate to cook something up for you, it would likely delete files or something else unpleasant. Here's a script I currently use to check if symlinks exist in a static directory and create them if they don't. You'd need to modify for recursiveness, though...

```
#!/bin/bash
# cpshortcuts by ngoonee, Jan 09

#modify the vars as appropriate to your use-case
SAVEDIR=/home/shortcuts/
APPDIR=/usr/share/applications/

#Check APPDIR for broken links, delete them
for FILE in $(ls $APPDIR | grep .desktop); do
	if [ -h $APPDIR$FILE ]; then
		if [ ! -e $APPDIR$FILE ]; then
			echo $APPDIR$FILE is a broken symbolic link, deleting...
			rm $APPDIR$FILE
		fi
	fi
done

#Check SAVEDIR for desktop shortcuts, link withink APPDIR, deleting pre-existing shortcuts with the same name.
for FILE in $(ls $SAVEDIR | grep .desktop); do
	if [ -e $APPDIR$FILE ]; then
		echo $APPDIR$FILE exists, deleting...
		rm $APPDIR$FILE
	fi
	ln -s $SAVEDIR$FILE $APPDIR$FILE
	echo $SAVEDIR$FILE linked to $APPDIR$FILE
done
```

I basically have one /home/shortcuts folder where I create all my short-cuts to the apps I've compiled from source, run from Wine, or run with my own script (which i save to /home/scripts, to be a bit off-topic). However, it's always easier to symbolically link this directory to /usr/share/applications (or ~/.local/share/applications, depending what you wish) for programs such as gnome-do to find the .desktop files easily.

Try it out. BASH scripting is very powerful, and a welcome relieve from the C++-programming I'm used to (I just know someone will mention Ruby etc., I've never gotten round to learning that, okay? So I wouldn't know how fantastic they are :) ).

---

