---
title: "Need help with Frets on Fire song editor"
date: 2008-06-30
forum: Gaming &amp; Leisure
---

### Post by Christopherius on 2008-06-30
I downloaded a song editor for frets on fire called eof. the link is here: [http://fretsonfire.wikidot.com/eof]("http://fretsonfire.wikidot.com/eof"). I'm not quite sure how to run or install the program. I tried the ./configure and make commands but they did not work. I would really like
to figure this out as it is alot easier to create songs this way.

Thanks for any help!

Chris

---

### Post by DoktorSeven on 2008-06-30
Apparently you grab the Linux source, go into the src directory and type:

```

make -f makefile.linux

```

You'll need some -dev stuff of course (liballegro at least, from what I see), just search synaptic or apt-cache search for the -dev packages.

Edit: Built, and there's a runtime dependency on **lame** and **oggenc** if you want to convert MP3s (sudo apt-get install lame vorbis-tools).  There's also an error that names the resulting file "targetdirectory\guitar.ogg" because of the Windows backslash thing.  Open "dialog.c" and go to around line 746 or so and change the line "strcat (syscommand, "\\");" to:

```

strcat (syscommand, "/");

```

---

### Post by Christopherius on 2008-07-01
thanks alot! that saved me hours of troubleshooting. I really appreciate it

---

### Post by 5of0 on 2008-08-06
I just downloaded the latest version (1.32) and all I had to do was install liballegro-dev and follow these instructions.  It was giving me strange errors before I did, though.

I looked at the source, and it looks like he's fixed the strcat windows issue - there are a bunch of #ifdefs now that switch between them, so for the latest version, the edit isn't necessary.

---

### Post by lexen on 2008-11-26
I'm can't seem to get it to work.  After I run the "make -f makefile.linux" command in the src folder, how do I get it to run?  I'm not really sure I did it right.



Thanks,
Lexen

---

