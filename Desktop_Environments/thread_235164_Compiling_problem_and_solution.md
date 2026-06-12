---
title: "Compiling problem and solution"
date: 2006-08-12
forum: Desktop Environments
---

### Post by Budreaux on 2006-08-12
Ok, I just worked through a problem I was having installing a program (advancemame for the curious - but the problem was not program specific).  Basically the problem was two fold.  First, after unzipping the tar.gz, I had to run the "./configure" command.  The first time I did this, I got the error 

```

configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```

after an extensive search through numerous forums, I found the following:

```

sudo apt-get install gcc

```

turns out I needed a compiler so after running the above line, and thinking I had fixed my problem, ran "./configure" again and got the following:

```

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

so once again, searched the web through various forums and finally came across this:

```

sudo apt-get install libc6-dev g++ gcc

```

apparently I also needed extra libraries (which if GCC doesn't work without them, then why is it not included with the GCC package).  Sooooooo, I ran "./configure" again and presto - it worked.  I just thought I would share this with everyone else.  It took quite a bit of time to figure all of this out, might as well save someone else the time.

Cheers!

---

### Post by fandelau on 2006-08-13
Oh man! I wish I ran into your thread a couple of days ago... Thanks!
Now I have to figure out this one:
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
I'll post when I find the answer...
Cheers!

PS BTW I'm trying to compile kxdocker 1.1.4 ... crossing my fingers and toes...

---

### Post by Nana on 2006-08-13
> **fandelau said:**
> Now I have to figure out this one:
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
I'll post when I find the answer...
Cheers!

PS BTW I'm trying to compile kxdocker 1.1.4 ... crossing my fingers and toes...
It looks like your system is missing some X development files.

Kxdocker is a KDE application, right? Try installing kdebase-dev.

---

### Post by fuzzmo on 2006-08-13
You are a star - thanks for the first and second part - was doing my head in.  Managed to install kdebase-dev through synaptic and voila!

Thanks dude!

---

### Post by scotty2hott2k on 2006-08-13
build-essential

---

