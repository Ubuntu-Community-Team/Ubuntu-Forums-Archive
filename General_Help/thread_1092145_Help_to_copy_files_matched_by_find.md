---
title: "Help to copy files matched by find"
date: 2009-03-10
forum: General Help
---

### Post by McRea on 2009-03-10
Hi, I need to copy the result of this research : find . -name *.png
into a new directory pngFiles made by me on the desktop.
How can I write this command on the shell?

Thanks

:popcorn:

---

### Post by unutbu on 2009-03-10
The command
```

find . -name *.png -exec cp {} ~/Desktop/pngFiles/ \;
```

will copy the png files to ~/Desktop/pngFiles/.

If you want to preserve the subdirectories of the original png files, then
you could use this command:```


rsync -avm --include='*.png' -f 'hide,! */' ./ ~/Desktop/pngFiles/
```

---

### Post by mr_git on 2009-03-10
One way is like this:

```

find . -type f -name '*.png' -exec cp -v {} ~/Desktop/pngFiles \;

```

---

### Post by McRea on 2009-03-10
with the command: find . -name *.png -exec cp {} ./Desktop/pngFiles

it returns : miss the argument of '-exec'

what's wrong?:(

---

### Post by unutbu on 2009-03-10
Don't omit the \; at the end of the command.

---

### Post by McRea on 2009-03-10
Now it works.. thanks

ps:OMG something really strange happened
I made the research with find from my home directory, and it has returned me
a lot of images that I have never seen before plus a lot of Images that I have just seen once on the web or something like that..

At the beginning of each of this png file there are strange long string with letters and numbers.

what's happened?:o

---

### Post by issih on 2009-03-10
Son't worry,its just pulling images out of your web cache, which presumably is located in your home drive somewhere, i'd guess somewhere in a hidden folder named .firefox or .mozilla, but I don't know off the top of my head.

All web browsers cache images,etc as a way to reduce load times for web pages. That find command just searched your home directory (including the hidden folders and therefore the cache) for png files, and not surprisingly, found some :)

The strange file names are simply because the web browser uses its own file naming structure, i'd guess based on hashing the url of a resource, so that it can quickly check if it has a file in the cache that matches the one it needs to load. Given that the program is quite happy with numbers rather than needing something that makes sense to a human being, that explains your odd filenames.

---

