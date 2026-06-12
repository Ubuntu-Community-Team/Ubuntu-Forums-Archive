---
title: "Command Line Question."
date: 2009-05-24
forum: General Help
---

### Post by rcayea on 2009-05-24
Is there a way from the command line (so I may later copy-paste and print in a word document) the list of programs (either installed from package manager or from what I have had to download myself) I have on my ubuntu system?

Thanks,
/R/

---

### Post by ad_267 on 2009-05-24
Not that I've found. If you haven't cleared out your cache of packages you can get a list of packages downloaded using "ls /var/cache/apt/archives/*.deb"

---

### Post by hesjnet on 2009-05-24
What about this:
[http://ubuntuforums.org/showthread.php?t=261366]("http://ubuntuforums.org/showthread.php?t=261366")

---

### Post by ad_267 on 2009-05-24
> **hesjnet said:**
> What about this:
[http://ubuntuforums.org/showthread.php?t=261366]("http://ubuntuforums.org/showthread.php?t=261366")

That lists all packages that are installed, including all of the packages included in the default installation. I'm not sure that's what the OP is after, although it might be useful.

---

### Post by niteshifter on 2009-05-24
Hi,

Why yes there is a way:

```
dpkg -l
```

Note: That is a lower case L, not the numeral 1. That command will list all packages installed.

You'll probably want use it like this:
```
dpkg -l > mypackages.txt
```

---

### Post by rcayea on 2009-05-24
Thanks for the suggestions. I will give them a try and post back any success.

/R/

---

### Post by rcayea on 2009-05-24
> **niteshifter said:**
> Hi,

Why yes there is a way:

```
dpkg -l
```

Note: That is a lower case L, not the numeral 1. That command will list all packages installed.

You'll probably want use it like this:
```
dpkg -l > mypackages.txt
```


The second option, (dpkg -l > mypackages.text, was exactly what I was looking for. 

Thank you!
/R/

Does anyone know how to mark a thread as SOLVED?

---

### Post by Iowan on 2009-05-24
> **rcayea said:**
> 
Does anyone know how to mark a thread as SOLVED?
[http://ubuntuforums.org/showthread.php?t=1044714]("http://ubuntuforums.org/showthread.php?t=1044714")

---

### Post by rcayea on 2009-05-24
thanks for the info about marking threads as solved.

---

### Post by oldos2er on 2009-05-24
Also run ```
sudo aptitude
``` for an ncurses interface package manager.

---

### Post by Simian Man on 2009-05-24
The dpkg solution will not do exactly what you said you want.  It will list the *packages* you've installed - not the programs.  There are a lot of packages that aren't programs (themes, data files, metapackages...) and there can be programs that aren't packages if you installed programs from source (or written your own).

A better solution (and more portable one) would be to look at all of the programs in your path.  A good start would be:
```

ls /bin /usr/bin /sbin /usr/sbin > myprograms.txt

```

You can also browse your programs by hitting tab twice quickly at the bash shell.

Of course it may be the case that you *want* the package list, but that isn't what you said.

---

### Post by rcayea on 2009-08-24
thanks for the last two tips! they are quite helpful. :)

---

