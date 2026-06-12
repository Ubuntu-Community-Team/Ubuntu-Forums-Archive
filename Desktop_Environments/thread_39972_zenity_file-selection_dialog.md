---
title: "zenity file-selection dialog"
date: 2005-06-07
forum: Desktop Environments
---

### Post by gdcondor on 2005-06-07
I just wrote a script based on Zenity which use this file-selection dialog : but by default it opens $HOME/Documents directory, is it possible to change it ? (not permanently but by adding a parameter to zenity or by changing a $PATH in my script)

thanks for your help

---

### Post by jazzer on 2005-06-07
[QUOTE=gdcondor]I just wrote a script based on Zenity which use this file-selection dialog : but by default it opens $HOME/Documents directory, is it possible to change it ? (not permanently but by adding a parameter to zenity or by changing a $PATH in my script)

thanks for your help[/QUOTE]

I am going to automatically presume you are writing a bash script...  Right before you execute zenity from the script add:

```
 pushd /full/path/to/directory 
```

That will set the bash scripts working directory and zenity opens in the current working directory.  If you want to go back to the previous directory you will have to use pushd again.

---

### Post by gdcondor on 2005-06-07
it's not working

and if I try in a terminal, pushd /my_dir/ effectively moves to my_dir but just after if I try "zenity --file-selection" it opens the dialog box in ~/Documents
:(

---

### Post by jazzer on 2005-06-08
[QUOTE=gdcondor]it's not working

and if I try in a terminal, pushd /my_dir/ effectively moves to my_dir but just after if I try "zenity --file-selection" it opens the dialog box in ~/Documents
:([/QUOTE]

Very odd, I do not have a ~/Documents directory, however after adding one zenity would only open the dialog box in ~/Documents.  However, on the upside, I found another way of specifying the directory for the dialog box.  :wink:  Try:

```
 zenity --file-selection --filename=/my_dir/ 
```

Make sure you add the / at the end of the directory name.

---

