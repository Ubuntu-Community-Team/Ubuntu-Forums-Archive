---
title: "Sort files into folders based on filename"
date: 2009-03-09
forum: General Help
---

### Post by svivian on 2009-03-09
I have a bunch of pictures, which I would like to sort into folders. The directory names would be the first few characters of the filenames themselves, e.g. img_001.jpg and img_002.jpg would go in the "img" folder, while pic_001.jpg and pic_002.jpg would go in the "pic" folder.

Are there any simple commands to do this kind of thing? Is *mv* isn't able to create folders? (I get "No such file or directory" with no options added.)

Maybe some kind of command line script or bash file is the way forward? Can anyone give me some pointers?

---

### Post by hatten on 2009-03-09
mkdir is the command for creating folders.
Google a bit, wildcards are useful

mkdir pictures
mv pic* pictures

---

### Post by svivian on 2009-03-09
I am aware of those commands, I was hoping for something a bit less manual. Your way, I have to manually create each folder individually (more than 50 of them), then do 50 commands to move the files.

Maybe I can grab substrings from the filenames and pass into the mkdir function?

---

### Post by svivian on 2009-03-09
OK I've cobbled this together, which will lists the folders I need to create:
```
ls | grep _000.jpg | sed 's/_000\.jpg//'
```

How can I pass this into mkdir? Piping doesn't work in this case...

---

### Post by ghostdog74 on 2009-03-09
don't have to pipe to grep. Use a loop
```

ls *_000.jpg | while read FILE
do
  FILE=${FILE/_000.jpg/}
  mkdir $FILE
done

```
don't have to use external command sed to replace strings.

---

### Post by ptruchon on 2009-05-28
What if there were more layers to the directory tree?  For example, I have a list of files with the following name pattern:

```
DIR1\DIR2\NAME
```

The directory names are not all the same length but are all separated by backslashes.  I'd like to create the directory tree and move all the files in their proper places while removing the path from the file name.

Any ideas?

Cheers!

---

