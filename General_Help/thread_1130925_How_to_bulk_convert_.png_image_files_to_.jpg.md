---
title: "How to bulk convert .png image files to .jpg"
date: 2009-04-20
forum: General Help
---

### Post by ubuntu1sttimer on 2009-04-20
Have a large number of .png image files that I need to convert to .jpg. They are 100-150 in each folder. So would like to do a folder at a time putting the .jpg copies in a sub folder.

It appears that ImageMagick's convert command should do it but have been unable to find a way to put them in a different folder. Or a different program is fine if it does a quality job.

If your way requires terminal mode, please include an example of the command.

---

### Post by Brucevdk on 2009-04-20
This question has probably been answered a thousand times before, but I'm too lazy to find them so I'll just think up of an answer. Here's how I'd do it:

```

find . -type f -name '*.png' | while read picture; do convert "$picture" "output/${picture/png/jpg}"; done

```

This will convert all pngs in the current directory to jpg in a subdirectory named output (this needs to exist before executing the command).

See man convert for what kind of options you can pass (quality etc.)

---

### Post by leandromartinez98 on 2009-04-20
Take a look at this post:

[http://ubuntuforums.org/showpost.php?p=7008245&postcount=5](http://ubuntuforums.org/showpost.php?p=7008245&postcount=5)

I think it is the most elegant solution. The example is for jpg to pdf, but it is the same for your case. You must only edit the command inside the function in order to
create the folders. Maybe a combination with the suggestion of Brucevdk will
be perfect.

---

### Post by kaibob on 2009-04-20
> **ubuntu1sttimer said:**
> Have a large number of .png image files that I need to convert to .jpg. They are 100-150 in each folder. So would like to do a folder at a time putting the .jpg copies in a sub folder....
If I understand correctly, you want to convert the PNG files in the current directory and only that directory and you want to place the JPG files in a subdirectory of the current directory. If that's correct, open a terminal window and navigate to the directory that contains the PNG files. Then, enter the following:

```
mkdir ./jpg_files ; for FILE in *.png ; do convert "$FILE" "./jpg_files/${FILE/%png/jpg}" ; done
```

Be sure to keep a backup of all files.

---

### Post by ubuntu1sttimer on 2009-04-20
Thanks all. Had searched on this subject but did not find anything that seemed to really do the job.

leandromartinez98, I tried that but managed to mess it up. Not the best with scripts or for that mater the command line. 


kaibob, that worked great. Knew there had to be a way but again, not knowing scripting, didn't know what I needed.

Great to have all the help here on the forums.

---

