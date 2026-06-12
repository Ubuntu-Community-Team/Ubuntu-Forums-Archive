---
title: "Screenshot script+gnome keybinding"
date: 2010-10-24
forum: Desktop Environments
---

### Post by Uriziel on 2010-10-24
```
#!/bin/bash

screenshot='screenshot';
nano=`date '+%d-%m-%y-%N'`;
extension='.png';
file="$HOME/.screenshots/$screenshot-$nano$extension";
#file="$HOME/.screenshots/screenshot-24-10-10-646659101.png";
scrot -s -b -q 75 $file -e 'gimp $f';

#if zenity --timeout=3 --title=='Edit with gimp?' --text=='Edit with gimp?' --question ; then
#gimp $file;
#fi

TEXT=$(curl -F "image"=@"$file" -F "key"="5d317f0bee23b282473522e1aa68f621" http://imgur.com/api/upload.xml | grep -Eo '<original_image>(.+?)</original_image>' | grep -Eo 'http://(.+?).png'); 

echo $TEXT | xclip -selection clipboard;
echo $TEXT | xclip;

firefox $TEXT;

echo "$screenshot-$nano$extension $TEXT" >> "$HOME/.screenshots/screenshotshistory";

notify-send -t 3000 "Screenshot ready";

exit 0;

```
I've found and edited screenshot script, it works fine.
I've added symlink to /bin/, it works fine.
Now, when I execute script it works fine.
But when I try using it with gnome-keybinding it doesnt work.
Well, basicly I have tested it in various ways, the only thing that doesn't seem to work is scrot, everything works fine, cept the most important thing. Any ideas why it doesn't work?

---

### Post by wxuyec on 2011-11-15
> **Uriziel said:**
> ```
#!/bin/bash

screenshot='screenshot';
nano=`date '+%d-%m-%y-%N'`;
extension='.png';
file="$HOME/.screenshots/$screenshot-$nano$extension";
#file="$HOME/.screenshots/screenshot-24-10-10-646659101.png";
scrot -s -b -q 75 $file -e 'gimp $f';

#if zenity --timeout=3 --title=='Edit with gimp?' --text=='Edit with gimp?' --question ; then
#gimp $file;
#fi

TEXT=$(curl -F "image"=@"$file" -F "key"="5d317f0bee23b282473522e1aa68f621" http://imgur.com/api/upload.xml | grep -Eo '<original_image>(.+?)</original_image>' | grep -Eo 'http://(.+?).png'); 

echo $TEXT | xclip -selection clipboard;
echo $TEXT | xclip;

firefox $TEXT;

echo "$screenshot-$nano$extension $TEXT" >> "$HOME/.screenshots/screenshotshistory";

notify-send -t 3000 "Screenshot ready";

exit 0;

```I've found and edited screenshot script, it works fine.
I've added symlink to /bin/, it works fine.
Now, when I execute script it works fine.
But when I try using it with gnome-keybinding it doesnt work.
Well, basicly I have tested it in various ways, the only thing that doesn't seem to work is scrot, everything works fine, cept the most important thing. Any ideas why it doesn't work?



I've got the same problem as you. I also post it here but nobody reply.
I found that you posted this on year ago, so that I know I am having no hope.

---

