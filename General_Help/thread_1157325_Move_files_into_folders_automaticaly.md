---
title: "Move files into folders automaticaly"
date: 2009-05-12
forum: General Help
---

### Post by stealth1236 on 2009-05-12
I have a very large video collection and i want to move each video into a self titled folder 
movieA.avi ----> movieA folder
movieB.avi ----> movieB folder
ETC.
i had a script for windows that did this but obviously it wont work so i am just looking for an equivalent type thing ( i would attach the script but i cant find it now, originally i found it on LifeHacker.com). it doesnt need any features except to just put files into folder, its an aweful lot of work to do this to 300+ files :)
thanks alot

---

### Post by lvleph on 2009-05-12
Deleted since this did bad things to my comp.

---

### Post by lvleph on 2009-05-12
Not exactly sure what happened but I wouldn't run that script. I ran it in the wrong directory and some how it deleted my desktop folder.

---

### Post by kaibob on 2009-05-12
If I understand correctly, you have a directory (say /home/stealth/videos) that contains 300 video files. You want to create 300 directories in /home/stealth/videos with each directory having the name of one of the videos. You then want to move each video into the directory that has the same name. 

So, the directory structure would be:

BEFORE
/home/stealth/videos (contains 300 movie files)

AFTER
/home/stealth/videos (contains 300 directories but no movies)
/home/stealth/videos/movieA (contains movieA.avi)
/home/stealth/videos/movieB (contains movieB.avi)
...and so on.

This is not difficult to do, but best to clarify first.

---

### Post by sisco311 on 2009-05-12
it's far from perfect but it works:
```
#!/bin/bash

if [ ! $1 ]; then
  echo usage: $0 /path/to/dir
  exit 1
else
  ls -1 $1 | grep .avi$ | \
  while read film; do
    echo mkdir -p \"${film%.avi}\"
    echo mv \"${film}\"  \"${film%.avi}\"
#   after testing the script uncomment the lines below :)
#   mkdir -p "${film%.avi}"
#   mv "${film}" "${film%.avi}"
  done
fi

exit 0

```

---

### Post by sisco311 on 2009-05-12
[http://ubuntuforums.org/showpost.php?p=7262886&postcount=8]("http://ubuntuforums.org/showpost.php?p=7262886&postcount=8")

---

### Post by stealth1236 on 2009-05-13
Perfect!! thanks alot i knew it probaby already had been done but i had no idea how to do it or what to search thank again.

---

### Post by Williamthecg on 2009-05-13
you could use WINE :P

---

### Post by lisati on 2009-05-13
> **sisco311 said:**
> [http://ubuntuforums.org/showpost.php?p=7262886&postcount=8]("http://ubuntuforums.org/showpost.php?p=7262886&postcount=8")

Thanks - duly bookmarked in case I need it (I have heaps of music, video and photo files, nearly time to get reorganizing them due to running out of room on my external HDDs)

---

### Post by sisco311 on 2009-05-13
I was bored so I wrote this script:
[php]#!/bin/bash

usage ()
{
  cat<<EOF

  usage: $0 [OPTIONS] PATH

  Move files in subdirectories. 

  OPTIONS:
    -e     ext1[,ext2...] comma separated list of file extentions
    -n     No Action: show what files would have been moved
    -h     display this help and exit

  NOTE:    flags after PATH are ignored
  This script is provided "as is" with no warranty whatsoever, you assume all 
   responsibilty of the consequences of use.

  License: void
   
EOF
}
     
action="true"

while getopts "e:nhd:" flag
do
  case $flag in
  e)
    txe=( $(echo "$OPTARG" | sed "s/\,/ /g") )
    ext=".$(echo "$OPTARG" | sed "s/\,/\$\|\./g")\$"
    ;;
  n)
    action=""
    ;;
  h)
    usage
    exit 0
    ;;
  ?) 
    usage     
    exit 1
    ;;
  esac
done

eval dirname='$'$OPTIND
if [ ! -d $dirname ]; then 
  echo "No such directory: $dirname"
  usage
  exit 1
fi 

let OPTIND+=1
if [  $(eval echo '$'$OPTIND) ]; then
  echo "Invalid option: $(eval echo '$'$OPTIND)"
  usage
  exit 1
fi
 
ext=${ext:-\*}
dirname=${dirname:-$(pwd)} 

[ "$ext" != \* ] && ls -1 $dirname | grep -E "$(echo $ext)" | \
while read file; do
  directory=$(echo $file | awk "{gsub(/$ext/, \"\"); print}")
  if [ "$file" != "$directory" ]; then
    echo mkdir -p \"${directory}\"
    [[ $action ]] && mkdir -p "${directory}"
    for i in ${txe[@]}; do
      [[ -f "$directory.$i" ]] && echo mv -b \"$directory.$i\" \"$directory\"
      [[ ( $action ) && ( -f "$directory.$i" ) ]] && mv -b "$directory.$i" "$directory"
    done
  fi
done

[ "$ext" = "*" ] && ls -1 $dirname | \
while read file; do
  directory=${file%.*}
  if [ "$directory" != "$file" ]; then 
    echo mkdir -p \"${directory}\"
    [ $action ] && mkdir -p "${directory}"
    echo mv -b \"$directory.*\" \"$directory\"
    [[ $action ]] && mv -b "$directory."* "$directory"
  fi
done

exit 0  
[/php]Use the -n flag to test the script.

---

