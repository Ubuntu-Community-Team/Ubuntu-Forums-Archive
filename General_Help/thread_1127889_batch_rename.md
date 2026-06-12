---
title: "batch rename"
date: 2009-04-17
forum: General Help
---

### Post by action_owl on 2009-04-17
I have an large amount of files that are in the format of:

filename-with-dashes spaces_ect.nes;1

I need to remove the:
;1
or the last two characters from every filename

how can i do this with from command line?

---

### Post by dtoronto on 2009-04-17
```
sudo mv -R filename-with-dashes spaces_ect.nes;1 filename-with-dashes spaces_ect.nes
```

---

### Post by action_owl on 2009-04-17
but the file names are all different,
its a ton of nes roms and I dont want to do each file individually

---

### Post by kaibob on 2009-04-17
This will do what you want:

```
rename -n 's/;1$//' *
```

The -n option does a dry-run and reports proposed changes. Substitute -v for -n to actually rename the files.

---

### Post by poing on 2009-04-17
This should work:
> for f in `ls *\;1`; do mv $f `echo $f | sed s/\;1//`; done
Probably there is a more elegant way though.
EDIT: @kaibob: Ah, too slow. Yours is way better!

---

### Post by iponeverything on 2009-04-17
I love to use awk to build a command line then I pipe it to sh for execution.

This will print out the command lines:

```
ls *\;1 |awk -F\; '{print "mv \""$0"\" \""$1"\""}'

```

to make it happen for real:

```
ls *\;1 |awk -F\; '{print "mv \""$0"\" \""$1"\""}'|sh
```

---

### Post by ghostdog74 on 2009-04-19
> **poing said:**
> This should work:

Probably there is a more elegant way though.
EDIT: @kaibob: Ah, too slow. Yours is way better!

don't use ls in a for loop. Its useless. Just use shell expansion

```

for file in *

```

---

### Post by action_owl on 2009-04-20
thanks kaibob, it worked great

---

