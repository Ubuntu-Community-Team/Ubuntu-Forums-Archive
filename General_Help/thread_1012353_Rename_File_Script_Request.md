---
title: "Rename File Script Request"
date: 2008-12-15
forum: General Help
---

### Post by Tarvok on 2008-12-15
I don't know if this is a total faux pas or not, but I was wondering if someone could write me up a simple script. I could probably do it myself... after hours of research, but I'm sure someone here could just plunk it out with little effort.

I've got a directory full of files, all of which have some extra characters at the end of the file name. I'm sure there's a simple way to just loop through all of them (including subdirectories) and strip those extra characters off. I just haven't the faintest clue how that would be done.

---

### Post by eBoxNet on 2008-12-15
check this : [http://ubuntuforums.org/archive/index.php/t-336897.html](http://ubuntuforums.org/archive/index.php/t-336897.html)

i think the second post will do the job.

---

### Post by kaibob on 2008-12-15
Could you post a few examples of the files in question and what extra characters you want removed from the file names.

---

### Post by Tarvok on 2008-12-15
data1.cab;1
setup.exe;1
autorun.inf;1

I think you get the picture.

For the record, I bought the game years ago, but lost the disks. Been getting the urge to play again. I don't even know if this can work, but every torrent is coming up like this. I don't know why.

---

### Post by kaibob on 2008-12-15
```
find /directory/name -name '*;1' -type f -exec rename -n 's/;1$//' '{}' ';'
```

Change /directory/name and then run the command in a terminal window. The -n option directs rename to do a dry run and report proposed changes. If all appears well, change -n to -v and rerun the command to actually rename the files.

---

### Post by ajcham on 2008-12-16
There are also several GUI apps available in the repos which can do batch renaming.  If you have Thunar installed you should already have an app by the name of Bulk Rename in your Accessories menu.

---

### Post by tfy on 2008-12-16
> **ajcham said:**
> There are also several GUI apps available in the repos which can do batch renaming.  If you have Thunar installed you should already have an app by the name of Bulk Rename in your Accessories menu.
 yes , very  good , thank  you

---

### Post by Tarvok on 2008-12-16
Thanks for the help. Bulk rename did the job. Now, it ultimately didn't help me get it running, but that's a question for another place. I still don't know why those .isos had a ;1 at the end of every file name.

---

### Post by SenHu on 2009-02-05
The following biterscripting script will do just that. To download biterscripting free, go to their website at biterscripting.com .

Save the script in a file called C:/X.txt. Start biterscripting interactive and call the script exactly as follows.

script "C:/X.txt" dir("C:/Something") len(50)

The above will rename all files in C:/something by removing all characters after the 50th character. All X.txt, C:/Something, 50 are examples. Use your own values in their place.

You can call this script on any directory you prefer. Or, you can create a master script to repeatitively call this script for several directories. You can do this in batch mode by calling biterscripting
from another program or DOS.

stex=string extractor, chex=character extracter, chin=character inserter, -p=preserve original string, ]=upto and including, etc. Do a help on commands to get the details. These are rather powerful editor commands.

Sen


# START OF SCRIPT

# Declare input arguments.
var str dir
var int len

# Collect a list of files matching the pattern.
var str list
find -f "*" $dir >$list

# The list of files is in $list. Process one at a time.
while ($list <> "")
do
  # Get the next file.
  var str file, path, old_name, new_name
  lex "1" $list > $file

  # Remove path. This will give us just the file name in $name.
  stex -p "^/^l[" $file > $old_name # After (but excluding) the last /

  # Remove all characters from file name after $len.
  var str chex_arg
  echo makestr(int($len)) "["   # Will create "50[" indicating to extract everything after 50th character.
  chex -p $chex_arg $old_name >$new_name
  # $new_name now has the name of the file curtailed to 50 characters.
  script SS_SlashBack.txt ospath($file) >$file

  # Rename $file to $new_name
  system rename $file $new_name

# END OF SCRIPT

---

