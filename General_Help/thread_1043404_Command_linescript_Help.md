---
title: "Command line/script Help"
date: 2009-01-18
forum: General Help
---

### Post by decahedron on 2009-01-18
I have a list of .flv files that I would like to convert to .avi files.
I can do this for singel files with 

   ffmpeg -i  filename.flv filename.avi

However, I would like to use a command or script that will do the whole list.  something like...

   ffmpeg -i  *.flv *.avi

This does not work because it provides an query asking to overwrite the second .flv file in the directory.  It has been years since I wrote a dos batch file and I am new to Ubuntu.  I would appreciate help.

Thankyou.

---

### Post by SPr on 2009-01-18
Try it with the -y option.
> 
-y  overwrite output files


---

### Post by mcduck on 2009-01-18
This should work, although you'll end with files named as something.flv.avi (you can just rename them later to remove the flv part):
```
for f in *.flv; do ffmpeg -i $f $f.avi; done
```

edit: using the -y switch, like SPr pointed out, would solve the name problem as well.

---

### Post by mssever on 2009-01-18
> **decahedron said:**
> I have a list of .flv files that I would like to convert to .avi files.
I can do this for singel files with 

   ffmpeg -i  filename.flv filename.avi

However, I would like to use a command or script that will do the whole list.  something like...

   ffmpeg -i  *.flv *.avi

This does not work because it provides an query asking to overwrite the second .flv file in the directory.  It has been years since I wrote a dos batch file and I am new to Ubuntu.  I would appreciate help.

Thankyou.
```
for i in *.flv; do
  ffmpeg -i "$i" "${i/flv}avi"
done
```

EDIT: This will produce proper filenames with no need to remove a .flv.

---

### Post by mssever on 2009-01-18
> **SPr said:**
> Try it with the -y option.
That won't help, because using * in both input and output is the wrong approach.

---

### Post by mcduck on 2009-01-18
mssever: Thanks for the ""${i/flv}avi"-part. I've been searching for a nice way to handle that kind of things without having to use awk or some other tool to parse the file names in scripts. :)

---

### Post by mssever on 2009-01-18
> **mcduck said:**
> mssever: Thanks for the ""${i/flv}avi"-part. I've been searching for a nice way to handle that kind of things without having to use awk or some other tool to parse the file names in scripts. :)
You can also use syntax like this:```
${i/flv/avi}
```That allows you to do substitutions at places other than the end: ```
~:$ i=foo.flv
~:$ echo "${i/o/bar}"
fbaro.flv
```

---

### Post by decahedron on 2009-01-18
Thanks for answering my question so quickly.  I am new to Linux and like using Ubuntu, I have even converted my wife, and it is nice to know the support is here when I need it.

---

