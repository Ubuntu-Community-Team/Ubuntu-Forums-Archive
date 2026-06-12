---
title: "[SOLVED] bash space character issues"
date: 2008-12-05
forum: General Help
---

### Post by fat_man_dan on 2008-12-05
I am attempting to copy all of the files that contain a certain work in and dump them into another directory. I have attempting to use the command
```
cp `tree -if | grep -i "FILENAME"` ~/destination_folder
```
but this can not seem to handle any file names with spaces in it. I have attempted changing the command to be
```
cp `tree -if | grep -i "FILENAME" **| tr " " "\ "**` ~/destination_folder
```
but that still does not work

Anyone got any suggestings on how I can get this working?

---

### Post by sisco311 on 2008-12-05
try:
```
IFS=$'\t\n'
cp `tree -if | grep -i "FILENAME"` ~/destination_folder
IFS=$' \t\n'
```

[list][*]set the IFS variable to tab and newline(don't treat spaces in filenames as special caracter)
[*]run the command
[*]set the IFS back to the default value(space, tab, newline)
[/list]
in one line:
```
IFS=$'\t\n' && cp `tree -if | grep -i "FILENAME"` ~/destination_folder && IFS=$' \t\n'
```

---

### Post by fat_man_dan on 2008-12-05
Thank you, that worked perfectly
You are a legend!!!

---

