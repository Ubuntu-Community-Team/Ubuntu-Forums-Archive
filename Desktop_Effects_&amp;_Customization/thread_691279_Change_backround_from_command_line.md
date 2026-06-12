---
title: "Change backround from command line"
date: 2008-02-08
forum: Desktop Effects &amp; Customization
---

### Post by ebsbox on 2008-02-08
Is there a command to change the background from the command line?

---

### Post by DaymItzJack on 2008-02-08
> **ebsbox said:**
> Is there a command to change the background from the command line?

from looking at this script:
```
#!/bin/bash
# script: change_backgrounds.sh - bash version
# version 2007.3.7
# description: randomly replace gnome background with one from a directory
# credits: David Loschiavo [http://www.djlosch.com], Steven Van Ingelgem
# license: GPL

bg_path=/mnt/archive/media/pics/backgrounds
extensions="jpg png gif jpeg JPG GIF PNG"
temp_bg_list=/tmp/bg_change_list

rm -f $temp_bg_list

for extension in $extensions
do
	find $bg_path -iregex ".*.$extension" >> "$temp_bg_list"
done

cnt=`wc -l "$temp_bg_list" | cut -f1 -d" "`
all_bgs=`echo \`expr $RANDOM % $cnt\``

selected_bg=`head -n$all_bgs "$temp_bg_list" | tail -n1`

logger "Changed desktop to: $selected_bg"

gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$selected_bg"
exit 0
```
[http://www.djlosch.com/article_Code:_Bash_Script_to_Change_Gnome_Background_Randomly_(Ubuntu](http://www.djlosch.com/article_Code:_Bash_Script_to_Change_Gnome_Background_Randomly_(Ubuntu))

I'm guessing it's the 
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$selected_bg"
``` line.

---

