---
title: "bash script help"
date: 2009-02-07
forum: General Help
---

### Post by Durrock on 2009-02-07
Hey all -
Could someone help me with a bash script to do the following?

I've got a directory, with all my music in in, organized by bandname/albumname/mp3 and /flac.  I realize now, that my music players can scan those directories, but I get two songs for each album, one flac, one mp3.

Is there an easy way (script) that'll move all the flac files out of that directory tree, into a new one (/music/bandname/albumname/flac) making sure to keep things organized?

thanks

---

### Post by geirha on 2009-02-07
```

cd /path/to/current/music/folder

# If you are in the correct dir, this should list all flac-dirs on the form:
# ./band/album/flac
find -type d -name flac  

# This should list albums on the form: ./band/album
find -type d -mindepth 2 -maxdepth 2

# If the above are correct, the following should create the band and album dirs under /music/:
find -type d -mindepth 2 -maxdepth 2 -exec mkdir -v -p /music/{} \;

# And this should move all flac dirs into the new tree:
find -type d -name flac -exec mv -v -i {} /music/{} \;

```

I recommend you read the man-pages for these commands:
```
man find
man mkdir
man mv

```

---

### Post by Durrock on 2009-02-07
> **geirha said:**
> ```

# And this should move all flac dirs into the new tree:
find -type d -name flac -exec mv -v -i {} /music/{} \;

```

Excellent - thank you very much. This helped immensely.  I didn't follow the above command though, what are the curly braces for?  

One last question - say I wanted to move the mp3s in each album out of the directory structure of /mp3/band/album/mp3/ to /mp3/band/album, could I do something like:


```


find -name *.mp3 -exec mv -v -i {}/music/ ??? \;

I am not sure how to recursively parse out each mp3 and mv it one level down?


```

---

### Post by geirha on 2009-02-08
> **Durrock said:**
> Excellent - thank you very much. This helped immensely.  I didn't follow the above command though, what are the curly braces for?  


The curly braces is replaced by the directory or file that find found.
As an example, let's say you have two albums:
```

$ find -type d -name flac
[COLOR="RoyalBlue"]./Metallica/Reload/flac[/COLOR]
[COLOR="SeaGreen"]./Britney Spears/Toxic/flac[/COLOR]

```

Then doing « find -type d -name flac -exec mv -v -i {} /music/{} \; » will run the following two commands:

```
mv -v -i [COLOR="RoyalBlue"]./Metallica/Reload/flac[/COLOR] /music/[COLOR="RoyalBlue"]./Metallica/Reload/flac[/COLOR]
mv -v -i [COLOR="SeaGreen"]./Britney Spears/Toxic/flac[/COLOR] /music/[COLOR="SeaGreen"]./Britney Spears/Toxic/flac[/COLOR]
```

> **Durrock said:**
> 
One last question - say I wanted to move the mp3s in each album out of the directory structure of /mp3/band/album/mp3/ to /mp3/band/album, could I do something like:


```


find -name *.mp3 -exec mv -v -i {}/music/ ??? \;

I am not sure how to recursively parse out each mp3 and mv it one level down?


```

That's a little bit harder. Not sure what the best way is, but this should work:
```
find -type d -name mp3 -print0 | 
while read -d $'\0' dir; do [COLOR="Red"]echo[/COLOR] mv -v -i "$dir"/* "${dir%/mp3}"; done

```

As the command is now, it will not actually move anything, it will just print the commands it intends to run. If the commands it intends to run looks correct to you, remove the [COLOR="Red"]echo[/COLOR] which I've marked in red.

---

### Post by Durrock on 2009-02-08
> **geirha said:**
> The curly braces is replaced by the directory or file that find found.
As an example, let's say you have two albums:
```

$ find -type d -name flac
[COLOR="RoyalBlue"]./Metallica/Reload/flac[/COLOR]
[COLOR="SeaGreen"]./Britney Spears/Toxic/flac[/COLOR]

```

Then doing « find -type d -name flac -exec mv -v -i {} /music/{} \; » will run the following two commands:

```
mv -v -i [COLOR="RoyalBlue"]./Metallica/Reload/flac[/COLOR] /music/[COLOR="RoyalBlue"]./Metallica/Reload/flac[/COLOR]
mv -v -i [COLOR="SeaGreen"]./Britney Spears/Toxic/flac[/COLOR] /music/[COLOR="SeaGreen"]./Britney Spears/Toxic/flac[/COLOR]
```



That's a little bit harder. Not sure what the best way is, but this should work:
```
find -type d -name mp3 -print0 | 
while read -d $'\0' dir; do [COLOR="Red"]echo[/COLOR] mv -v -i "$dir"/* "${dir%/mp3}"; done

```

As the command is now, it will not actually move anything, it will just print the commands it intends to run. If the commands it intends to run looks correct to you, remove the [COLOR="Red"]echo[/COLOR] which I've marked in red.


Thank you very much - everything worked great!  Gotta learn more scripting obviously - this saved me a lot of time.  
I also did the following to remove the now empty mp3 directories 

```

find -type d -name mp3 -exec rm -r {} \;

```

Thank you again.

---

### Post by geirha on 2009-02-08
> **Durrock said:**
> Thank you very much - everything worked great!  Gotta learn more scripting obviously - this saved me a lot of time.  
I also did the following to remove the now empty mp3 directories 

```

find -type d -name mp3 -exec rm -r {} \;

```

Thank you again.

Very good! However, rm -r is a bit dangerous to use. In this case you had empty directories you wanted gone, so doing:

```
find -type d -name mp3 -exec rmdir {} \;
```
would've been safer, because rmdir will refuse to remove a directory if it is not empty:

```

$ rmdir ~/Desktop
rmdir: failed to remove «/home/geirha/Desktop»: Directory not empty

```

So if for some reason a file or two was left in one of the mp3 dirs, they're gone now. The likely hood of that is slim though, but it's good practice to use rmdir rather than rm when removing empty directories.

find also has it's own way of deleting files and directories, the -delete option, and that will also refuse to remove non-empty directories.
```
find -type d -name mp3 -delete
```

One last thing you should be aware of when using the terminal, is the man command. If you have a command you want to run, found by googling or something like that, but you're not sure what exactly it does, read the man-page of the command. For the find command, you would do:
```
man find
```

---

