---
title: "Stupid Shell Script Problems"
date: 2009-05-15
forum: General Help
---

### Post by dbsoundman on 2009-05-15
So I decided to write a shell script which addresses an issue I have with my digital camera naming all its jpeg files as .JPG instead of .jpg. This is my script:

```
#! /bin/bash
gnome-terminal -x rename 'y/JPG/jpg/' *

```

The "rename 'y/JPG/jpg/' *" part works fine as it is in the terminal, but whenever I try to run this script, I get a "command not found" error, and if I put a "./" in front of it, I get "No such file or directory.". I moved the script I wrote to /home/dan/bin/, where my other working scripts are so that I could call it without a path or the ./ , and I did of course chmod +x it. What could be wrong with this script?

Thanks,
Dan

---

### Post by spiderbatdad on 2009-05-15
should work fine if you name your script whatever.sh then run the command as```
whatever.sh
```Or remove the .sh and just run it with the program name. But why gnome-terminal -x?

---

### Post by dbsoundman on 2009-05-15
Good question...I suppose the gnome-terminal -x part might not be necessary :oops:. I haven't written a lot of these yet so I don't always think it through. I will try that and see if that solves it.

-Dan

---

### Post by spiderbatdad on 2009-05-15
to check your PATH, run ```
$PATH
```and look for /home/dan/bin. I probably should have just mentioned, no need for the gnome-terminal thingy. I am no shell script wizard either. My scripts are of about the same level of complexity.

---

### Post by dbsoundman on 2009-05-15
Thanks! I just checked it out, the path is fine, but taking away the gnome-terminal -x part made it work!

-Dan

---

### Post by kanikilu on 2009-05-15
Maybe I'm misunderstanding what the problem is here, but if you are making a shell script, is there a reason you are using **gnome-terminal -x**? Why not just do the rename and be done with it? Also, I think you want to substitute in that rename, right?

```
rename -v s/JPG/jpg/ *
```

Also, if you want to see the output, you could do something like this:

```
gnome-terminal -e "sh -c 'rename -v s/JPG/jpg/ * && bash'"
```

I don't know why you're getting "command not found" or "no such file or directory", though, it sounds like you did that part right (put it in ~/bin and make it executable).

// Edit - nevermind, it looks like you got it...

---

