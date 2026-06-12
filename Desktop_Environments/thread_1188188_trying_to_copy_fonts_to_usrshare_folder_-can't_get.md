---
title: "trying to copy fonts to usr/share folder -can't get code right"
date: 2009-06-15
forum: Desktop Environments
---

### Post by tpgames on 2009-06-15
How does one copy all files in jyzrxal/.fonts to usr/share/fonts/truetype?
I know cp means copy, but I can't get anything else correct. Do I need to select all of the fonts in .fonts using select all command? nothing is in cache directory. 
Thanks!:D

Update: mv *ttf *TTF /usr/share/fonts/truetype  
gives me 
mv: cannot stat '*ttf': no such file or directory
It can't stat *TTF either.
basically everything it says to do at ghack.net doesn't work. 

The actual file path is:
/usr/share/fonts/truetype

and for the fonts I uploaded from cd:
/jyzrxal/.fonts

---

### Post by tpgames on 2009-06-15
This is the last few stuff I tried: 
```

root@jyzrxal-desktop:/home/jyzrxal# cp [fonts] /usr/share/fonts/truetype
cp: cannot stat `[fonts]': No such file or directory
root@jyzrxal-desktop:/home/jyzrxal# cp [/jyzrxal/.fonts] /usr/share/fonts/truetype
cp: cannot stat `[/jyzrxal/.fonts]': No such file or directory
root@jyzrxal-desktop:/home/jyzrxal# cp [.fonts] /usr/share/fonts/truetype
cp: cannot stat `[.fonts]': No such file or directory
root@jyzrxal-desktop:/home/jyzrxal# mkdir ~/.fonts
root@jyzrxal-desktop:/home/jyzrxal# cp ~/.fonts
cp: missing destination file operand after `/root/.fonts'
Try `cp --help' for more information.
root@jyzrxal-desktop:/home/jyzrxal# cp [font file] ~/.fonts
cp: cannot stat `[font': No such file or directory
cp: cannot stat `file]': No such file or directory
root@jyzrxal-desktop:/home/jyzrxal# cp [.fonts] ~/.fonts
cp: cannot stat `[.fonts]': No such file or directory
root@jyzrxal-desktop:/home/jyzrxal# 

```

---

### Post by Bachstelze on 2009-06-15
```
sudo cp .fonts/*ttf /usr/share/fonts/truetype
```

---

### Post by tpgames on 2009-06-15
Thanks! That worked I believe. I at least get no error message. :popcorn:

---

### Post by Jekshadow on 2009-06-15
```
sudo cp <directory>/*.ttf /usr/share/fonts/truetype
```

replace <directory> with the directory you want to copy from. If you are dealing with the current directory your terminal is in, just use:

```
sudo cp *.ttf /usr/share/fonts/truetype
```

Explanation of the code:

**sudo**
Sudo runs the following command as the user "root", allowing it access and modify restricted system files.
*Usage: *sudo [command] [arguments]


**cp**
CP copies files from one directory to another
*Usage: *cp [file/files] [destination]

***.ttf**
Tells copy to copy all files ending with .ttf.

**/usr/share/fonts/truetype**
Tells copy where to copy the files to.

---

### Post by tpgames on 2009-06-15
I had found a site that had the wrong code for my setup. I found that I had to do *ttf and *TTF separately. 

The part I had issues with was getting the format correct for the directory the folder was in. 

Thanks again everyone!

---

