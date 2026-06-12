---
title: "Read Greek - Nautilus script"
date: 2010-06-03
forum: Desktop Environments
---

### Post by bkbilly on 2010-06-03
When I create on windows a text file in Greek, It doesn't recognize it with Ubuntu...
So I created a script:
```
#!/bin/bash
fileName="$@"
fileNoExt=$(basename "$fileName")
fileType=$(file "$fileNoExt")
fileText=$(echo "$fileType" | cut -d ':' -f2 | grep 'text')


if [`echo "$fileText"` == ""]
then
	zenity --error --title "ERROR" --text "     Empty File \n\t    or \nFile not supported"
else
iconv -f WINDOWS-1253 -t UTF-8 "$fileName" > /tmp/"$fileNoExt"
gedit /tmp/"$fileNoExt"
fi
```

Create an **SH** file and paste the above on the file.
Make it executable by **right click** -> **Properties** -> **Permissions** tab -> tick **Allow executing file as program**.
Place the file to *~/.gnome2/nautilus-scripts*

---

### Post by K.Mandla on 2010-06-13
Moved to Desktop Environments.

---

