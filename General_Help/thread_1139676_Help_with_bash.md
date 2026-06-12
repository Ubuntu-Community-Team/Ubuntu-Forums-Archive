---
title: "Help with bash"
date: 2009-04-27
forum: General Help
---

### Post by jmvidalvia on 2009-04-27
I am trying to write a script and I need to get the name of the files as a variable but without the complete structure of directories, just their names.
I mean,
"/home/usr/file.txt" is not valid for me.
"file.txt" would be ok.

I triend with find, ls, xargs, etc.. and always get the complete structure.
Thanks!

---

### Post by kaibob on 2009-04-27
There are a lot of ways to do what you want, and the method used depends in large part on the shell script, but one option is to use the basename utility. For example, enter the following in a terminal window:

FILE=$(basename /home/usr/file.txt) ; echo $FILE

---

### Post by jmvidalvia on 2009-04-27
Nice solution!
Thank-you!

---

### Post by jmvidalvia on 2009-04-29
> **kaibob said:**
> There are a lot of ways to do what you want, and the method used depends in large part on the shell script, but one option is to use the basename utility. For example, enter the following in a terminal window:

FILE=$(basename /home/usr/file.txt) ; echo $FILE

Just a little bit more of help: what about blank spaces inside the name...?
Here is my little code:
```
#!/bin/bash
DIR="/home/datos/envios/pdf/in"
DEST="/home/datos/envios/pdf/out"
FONDO="/home/datos/envios/pdf/fondos/fondo_desa.pdf"
if ! [ -z "`ls -A $DIR 2>/dev/null`" ]
then
        for FILE in `find $DIR -name *.pdf -type f -print0 | xargs -0`
do
        NAME=$(basename $FILE)
        pdftk $FILE background $FONDO output $DEST/$NAME
        rm $FILE
done
fi

```
It crashes when *output $DEST/$NAME* uses only a part of the complete name due to spaces.
Any ideas?
Thanks!

---

### Post by John Cheng on 2009-04-29
You may want to put the $FILE variable in quotes, i.e.,

```

    rm "$FILE"

```

---

### Post by slakkie on 2009-04-29
> **John Cheng said:**
> You may want to put the $FILE variable in quotes, i.e.,

```

    rm "$FILE"

```

This works great for files with spaces.

---

### Post by kaibob on 2009-04-29
I agree with John. The following illustrates this issue:

> $ FILE="/dir name/file name" ;  NAME=$(basename $FILE) ; echo $NAME
basename: extra operand `name'
Try `basename --help' for more information.

$ FILE="/dir name/file name" ;  NAME=$(basename "$FILE") ; echo "$NAME"
file name

---

### Post by jmvidalvia on 2009-04-29
Thanks for your reply, but..I am afraid the problem comes before:
```
 for FILE in `find $DIR -name *.pdf -type f -print0 | xargs -0`
echo $FILE

```

echo sends the name separated: I tried ", ` and ', with no success.
Thanks for your help.

---

### Post by jmvidalvia on 2009-04-29
> **kaibob said:**
> I agree with John. The following illustrates this issue:

Thanks! :)
But, how to use it with the "for" instruction?
Thanks for your help.

---

### Post by Brandon Williams on 2009-04-29
Try this:
```
#!/bin/bash
DIR="/home/datos/envios/pdf/in"
DEST="/home/datos/envios/pdf/out"
FONDO="/home/datos/envios/pdf/fondos/fondo_desa.pdf"
if ! [ -z "`ls -A $DIR 2>/dev/null`" ]
then
    find $DIR -name '*.pdf' -type f -print0 | xargs -0 | while read FILE
    do
        NAME=$(basename "$FILE")
        pdftk "$FILE" background $FONDO output "$DEST/$NAME"
        rm "$FILE"
    done
fi
```

---

### Post by kaibob on 2009-04-29
> **jmvidalvia said:**
> Thanks! :)
But, how to use it with the "for" instruction?
Thanks for your help.
I would simplify the script as follows:

```
#!/bin/bash

DIR="/home/kaibob/temp/in"
DEST="/home/kaibob/temp/out"
FONDO="/home/kaibob/temp/background.pdf"

find "$DIR" -iname '*.pdf' -type f | while read FILE ; do
NAME=$(basename "$FILE")
pdftk "$FILE" background $FONDO output "$DEST/$NAME"
rm "$FILE"
done
```

If all of the input files are located in one directory, a simpler alternative that omits the find commmand is:

```
#!/bin/bash

DIR="/home/kaibob/temp/in"
DEST="/home/kaibob/temp/out"
FONDO="/home/kaibob/temp/background.pdf"

cd "$DIR"

for FILE in *.pdf ; do
pdftk "$FILE" background $FONDO output "$DEST/$FILE"
rm "$FILE"
done
```

I changed the paths in the above to test the scripts

---

### Post by jmvidalvia on 2009-04-30
What an elegant solution!
Works fine.
Thank you very much everybody for your help!

---

