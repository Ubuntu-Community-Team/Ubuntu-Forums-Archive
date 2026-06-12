---
title: "Extract rpm"
date: 2005-12-26
forum: Desktop Environments
---

### Post by dbassett on 2005-12-26
How do I extract a RPM file using ubuntu?
Do I install or extract a rpm?

---

### Post by kaamos on 2005-12-26
You can install an rpm with alien
```
sudo apt-get install alien
```
Then to the file you have:
```
sudo dpkg -i the_name_of_the_file.rpm
```

---

### Post by cstudent on 2005-12-26
I think the second part should be:

```

sudo alien -i packagename.rpm

```

---

### Post by kaamos on 2005-12-26
Whoops, shouldn't be watching tv at the same time when posting! Sorry about that.

---

### Post by dbassett on 2005-12-26
What about installing a tar.gz that has already been extracted do I point to the .sh file?
Where will they get installed?

---

### Post by Sutekh on 2005-12-26
There's no 'one' way to install from a tar.gz, because it depends on what's in the archive. 

First I'd check to see if there is a readme, or similar.

If the tar.gz involves compiling from source, you should try these instructions too, check out Section 4

[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

The compiling usually ends up with one file for running the application, it'd probably be in the directory you compiled it from.  Sometimes a location is specified in the makefile too.

---

### Post by dbassett on 2005-12-26
Well, I've tried all the methods on each typ of file from
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)
but have not been able to install any yet.

Now that I'm here, I remember this is the reason I stopped using Redhat too

---

### Post by Sutekh on 2005-12-26
Yeah I stay away from compiling from source when possible.
What is the program you are trying to install?

---

