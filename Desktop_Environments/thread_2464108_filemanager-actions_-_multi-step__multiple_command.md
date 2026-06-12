---
title: "filemanager-actions - multi-step / multiple commands"
date: 2021-06-24
forum: Desktop Environments
---

### Post by revm on 2021-06-24
I am working in filemanager-actions to add the ability to right-click on a PDF file and export each page to a png file. I have this working with pdftoppm. What I would really like to make it do is to right-click on the file and the following would happen:

1) make a directory the same name as the PDF file (without the PDF extension in the folder name)
2) covert the PDF to pngs and have them outputted into the new folder

Does anyone know if this is possible with filemanager-actions? I was trying to make a bash script (or gnome-shell script/extension), but I am not familiar with that kind of scripting and was not having any success. I appreciate any advice, ideas, etc. Thank you in advance!

Blessings,


RevM

---

### Post by him610 on 2021-06-25
You might want to read the suggestions on this website - [https://superuser.com/questions/185880/how-to-convert-a-pdf-document-to-png/185886]("https://superuser.com/questions/185880/how-to-convert-a-pdf-document-to-png/185886")
The third suggestion down that uses *imagemagik* 
It has been awhile, but I have used it before.

---

### Post by vanadium on 2021-06-26
Filemanager-actions is not anymore available in Ubuntu 21.04. So your investments may not be future proof. Nautilus scripts, however, continue to work and also works reasonably well in this user case. Anyway, for what you wish, i.e. chaining different tools, a minimum of scripting will be required.

---

### Post by revm on 2021-06-26
> **vanadium said:**
> Filemanager-actions is not anymore available in Ubuntu 21.04. So your investments may not be future proof. Nautilus scripts, however, continue to work and also works reasonably well in this user case. Anyway, for what you wish, i.e. chaining different tools, a minimum of scripting will be required.

I had this feeling and was trying to look into writing/creating Nautilus scripts but did not get too far. The commands I am using in filemanager-actions are:

[COLOR=#000000]1) make a directory the same name as the PDF file (without the PDF extension in the folder name) = [/COLOR]**/bin/mkdir %w (or /bin/mkdir file1)**
[COLOR=#000000]2) covert the PDF to pngs and have them outputted into the new folder **= **[/COLOR][B]/bin/pdftoppm -png %f %d/%w/%w (or /bin/pdftoppm -png /path/to/file1.mid /path/to/file1/file1)

[/B]
Do you know if I can do something similar with the Nautilus scripts in terms of using the variables (or similar ones)? And do you have a resource for getting started with Nautilus scripts that you would recommend? I used to work in IT and program (mostly web programming) so I feel like I can follow examples pretty easily, but also do not want to break anything, lol.

Thank you in advance!

Blessings,


RevM

---

### Post by vanadium on 2021-06-27
I have following script which I ripped shamelessly from somewhere else, which converts selected bitmap graphics to PDF's.

```

#!/bin/bash
NAME=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
while read line
do
	[ -z "$line" ] && echo no || convert -density 96 "$line" -quality 50 "$line"_bitmap.pdf
done < <(echo "$NAME")

```

Put this script (marked as "executable") under ~/.local/share/nautilus/scripts and it will appear as an entry under a right-click "Scripts" menu. The name of the script is used as the menu item, so give it a pretty name. An extremely nice feature is that you can define an accelerator, by prepending the letter with _. For example, the script "Convert PDF to _lowres bitmap PDF" can be selected with "l", allowing for fast keyboard only access: once the file is selected, Shift+F10, s l would launch the script. 

The current directory of any launched script is the directory of the file you right-clicked.

It is less integrated and more simple than file manager actions. For one, the options will appear even on files types where they are not relevant. If needed, you have to check the validity of the file in the script itself. A file must be selected for scripts to be available, also when the actual script does not need a file.

---

