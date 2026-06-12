---
title: "Nautlius Action + Script help"
date: 2009-06-03
forum: General Help
---

### Post by TombstoneX on 2009-06-03
Im trying to make a script to extract file to: specified_location/User_Entered_Name when right clicked on and launched using Nautlius Action,

Here is the script i have wrote, can anyone see where i went wrong?

```
#!/bin/bash
#
# 7z movie extractor

base_folder=`basename $1`
file_name=$1

# Make the entry the name of the base folder name
if user_entry=$(zenity --entry --text="Name of Movie:" --entry-text="$base_folder")
then
/usr/bin/7z e $file_name -o/media/Old/****/Movies/"$user_entry" *.avi | zenity --progress --pulsate --title "Please Wait" --text $"Extracting $file_name"
zenity --info --title "Extracting Complete" --text "The file $file_name has been installed"
else
zenity --info --title "Extracting aborted" --text "The file $file_name was not installed"
exit 1
fi
```

---

