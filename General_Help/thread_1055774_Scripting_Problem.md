---
title: "Scripting Problem"
date: 2009-01-31
forum: General Help
---

### Post by thestig_992 on 2009-01-31
Im writing a script that checks if mp3 files exist in a folder, but the script keeps getting stuck at line 18, the fi

```
if [ find $FROMDIR -name '*.mp3' && find $FROMDIR -name '*.MP3' ]
then
	echo "No MP3 Files Exist In This Directory or Subdirectories"
	read -p "Press any key to quit"
	exit
fi
```

Actually trying to find if no mp3s exist, but for now just trying to troubleshoot the command...

Anyone know a solution?

UPDATE: Second question, when i move (in gui) a 'folder x' into 'folder y', and folder y contains a directory called 'folder x' I get a prompt to ask me if i would like to skip or merger or cancel etc...

When i do 
```
mv -t foldery folderx
``` though i get an error that says 
```
mv: cannot move `Black Ice/' to `temp/Black Ice': Directory not empty
```
where black ice is "folder x"

How do i tell mv to merge the directories like in gui?

UPDATE: found a replacement command:
```
rsync -arR Black\ Ice/ temp/ --remove-sent-files --ignore-existing --whole-file
```

---

### Post by croto on 2009-01-31
How about something like
```

if [ "$(find $DIRECTORY -iname '*mp3' 2>/dev/null)" == "" ]; then
	echo "No MP3 Files Exist In This Directory or Subdirectories"
	read -p "Press any key to quit"
	exit
fi

```

I'm not sure it's the most robust solution, you should test it on empty directories, non-existent $DIRECTORY, trying to traverse directory without enough permissions, etc. I guess it works. Take into account it's saturday morning after going out for drinks...

---

