---
title: "script to change part of file-name"
date: 2006-04-30
forum: Desktop Environments
---

### Post by jasplund on 2006-04-30
my camera poduces folders depending on date.


e.g. 1016047 or 1036047

I would like to make a script (nautilus-script) that automatically removes 101, 102 or 103 from the filename and replaces it with 0.

I already have a nautilus-script that removes the *.thm files in the folders. would it be possible with one script that makes both these things?

---

### Post by aysiu on 2006-04-30
If you had 1016047 and 1026047, and then did a replace on those first three digits, wouldn't you end up with two folders with the same name?

1016047 => 06047
1026047 => 06047

---

### Post by jasplund on 2006-04-30
[QUOTE=aysiu]If you had 1016047 and 1026047, and then did a replace on those first three digits, wouldn't you end up with two folders with the same name?

1016047 => 06047
1026047 => 06047[/QUOTE]

well it was just and example. I used the same date. and it should me 27 at the end.

I want 10160427 to be 060427
10160320 to be 060230
10360513 to be 060513 and so one.

a dream would be if it in addition could pop up a box where I can write a specific thing like this:

I have a folder called 10160427 I right-click on it and start the nautilus script. a box pop-ups and a write "in the forest" in the box and click ok --> the folder is now called "060427  - in the forest" and addition all *.THM files are removed.

would this be possible?

---

### Post by IYY on 2006-04-30
It can be easily done using sed (but look at aysiu's words of caution!)

```

for x in *10*
do
      name=`echo $x | sed -e "s/101\|102\|103/0/g"`
      mv $x $name
done

```

---

### Post by jasplund on 2006-04-30
[QUOTE=IYY]It can be easily done using sed (but look at aysiu's words of caution!)

```

for x in *10*
do
      name=`echo $x | sed -e "s/101\|102\|103/0/g"`
      mv $x $name
done

```[/QUOTE]

thanks I can't get it to work though

---

### Post by IYY on 2006-04-30
What do you mean? Need more details than that.

Also, for your dialog box, you'll need to use gdialog --inputbox. It writes the input to standard error.

---

### Post by jasplund on 2006-04-30
[QUOTE=IYY]What do you mean? Need more details than that.

Also, for your dialog box, you'll need to use gdialog --inputbox. It writes the input to standard error.[/QUOTE]


I wrote this:

#!/bin/sh

for x in *10*
do
      name=`echo $x | sed -e "s/101\|102\|103/0/g"`
      mv $x $name
done


and put it in the nautilus-scripts-folder and made it executable. When I start the script in a folder containing a folder called 10160424 nothing happened

---

### Post by Ramses de Norre on 2006-04-30
Start the script from terminal, you can see error messages then.

---

### Post by jasplund on 2006-04-30
[QUOTE=Ramses de Norre]Start the script from terminal, you can see error messages then.[/QUOTE]


mv: cannot stat `*10*': No such file or directory

---

### Post by xenmax on 2006-04-30
It means exactly that - there are no such files or directories.
Either running it from nautilus already did the job for you or you are in wrong directory when you are running script in terminal.
Did you check the folder contents after first attempt (reload in nautilus?)?

---

### Post by jasplund on 2006-04-30
It works like a normal script but not as a nautilus script

---

