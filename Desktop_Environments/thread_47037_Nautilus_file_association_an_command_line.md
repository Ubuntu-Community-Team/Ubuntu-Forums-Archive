---
title: "Nautilus file association an command line"
date: 2005-07-07
forum: Desktop Environments
---

### Post by rastaman on 2005-07-07
I made a script that runs par2 to verify and repair. I want to have Nautilus to run this script in a terminal window, and keep that terminal open because i need to see all the output.
what i tried was right click one of my *.par2 files click properties. then went to "Open With" tab, click add button. and put in the "Use a custom command" box:
```

'/usr/local/bin/par2-r' $1 $1

```
I put 2 $1 because the script needs 2 command lines parameters, (i know this is not quite right.  but what are the gnome things i can use to give it, in KDE I think I used %d for the directory, and %f for the filename. The first parameter is the path to the file and the second is the file name. this is because the par2 program needs to be run in the directory where the .par2 file is so i have to “cd” to it first.
Here is the script:
```

#!/bin/sh
cd "$1"
/usr/local/bin/par2 r "$2"

```
this was easy to setup in KDE but I don't know what to use for path and filename to send the to the script.  Currently it just does not seem to be doing anything when i double click a par2 file.

---

### Post by poptones on 2005-07-07
You want to do a nautilus script. 

[http://www.gnome.org/projects/nautilus/](http://www.gnome.org/projects/nautilus/)

If you really want to watch a progress box then leaving the terminal window open I will leave up to you, but here is the basic operation you described
```

#!/bin/sh
_DIR="$#" #this is the first selected file passed from nautilus
cd "${_DIR%/*}" #pass the filepath portion of DIR
/usr/local/bin/par2 r "${_DIR##/*}" #pass the filename portion of DIR
if [[ $? -gt 0 ]]; then 
 gdialog --msgbox "there was an error repairing $_DIR"
else
 gdialog --msgbox "$_DIR repair complete"
fi

```
You could also just redirect the output to a log file and have gdialog open it if there's an error. Again I'll leave that up to you; watching progress meters really isn't my thing, it kinda defeats the simplicty of the gui :)

---

### Post by rastaman on 2005-07-07
thanks for replaying.
OK I read-up on nautilus scripts. the one you posted will not work right for me. the $# just returns a "1" so changed it to $1 but that just returns the filename, don't know if it will return more than one filename. anyway i guess its executes in the directory that nautilus is in. It works OK like that but I need to see the output.

So I changed it a bit to open gnome-terminal and execute it. also found in another script how to get the directory.

EDIT:  The terminal just pops up and goes away be for I can see anything so its not running the par2 command.  what could be wrong here? 

```
#!/bin/sh
#get the directory.  from script gnome2-terminal-here
dir="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"

#this is the command i want to execute
# but how do i get double quotes in the string around $1 ?
runpar2="/usr/local/bin/par2 r "$1"" 

#test  show me what the strings have
gdialog --msgbox "ok i will open a terminal here ($dir) and run ($runpar2)"

gnome-terminal --working-directory="$dir" --execute "$runpar2"

```

---

### Post by rastaman on 2005-07-07
ok i looked at gnome-terminal command-lines again and if i use -e or --command insted of --execute it will run i can see it process. 

but now the big thing how to keep the terminal open after the command stops. I didn't see any command-line switches for that and when i try to modify runpar2 to something like
runpar2="/usr/local/bin/par2 r "$1" && read"
It just gives me a msgbox "All commands are complete" when i click ok it flashes the terminal window but does nothing ang goes away. :???:  :???:

---

### Post by rastaman on 2005-07-08
well still have not found a way to open a terminal and run it from there keeping the terminal open. 

But here is the next best thing :wink: , if anyone else wants it.
It does not open a terminal but runs par2 and redirects the output to a tempfile in /tmp.  Then if there was an error it shows the tempfile in gedit.  If not it shows a messagbox with success.  Then removes the tempfile.

par2-r
```
#!/bin/sh
#this is a bash script to be used with Nautilus to run par2 and repair your files.
#  by  rastaman 
#     lord underscore illogical at yahoo dotty com
#you will need par2cmdline installed in /usr/local/bin get it at http://parchive.sourceforge.net/
#

#get the directory.  from script gnome2-terminal-here
dir="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"

#get the par2 file name
par2file="$1"

TMPFILE=`mktemp -q /tmp/"$USER".par2.output.XXXXXX`
if [ $? -ne 0 ]; then
        echo "$0: Can't create temp file, exiting..."
        exit 1
fi

#goto the directory
cd "$dir"

#run par2 repair and send stdout and stderr to TMPFILE
# 2>&1 redirects stderr to stdout, it must be at end of line
/usr/local/bin/par2 r "$par2file"   > "$TMPFILE" 2>&1

if [[ $? -gt 0 ]]; then
  #show the output so we can see how many more par2 files we need
  gedit "$TMPFILE"&
else
  #just show a message box saying success
  gdialog --msgbox "$dir/$par2file repair completed successfully"
fi

#remove the temp file, must sleep 1 second so gedit can load it first
sleep 1
rm -f "$TMPFILE"


```

---

### Post by poptones on 2005-07-08
LOL. And there ya go...

*You could also just redirect the output to a log file and have gdialog open it if there's an error. *

You'll get it. You're already on your way!

---

### Post by chadk on 2006-06-23
COOL. Thanks ;)

---

