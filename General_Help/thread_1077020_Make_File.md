---
title: "Make File"
date: 2009-02-21
forum: General Help
---

### Post by RedSingularity on 2009-02-21
Everytime i try to install a tar.gz or a tar.bz2 i get this message  ```
No targets specified and no makefile found.  Stop.
```  How can i fix this problem?

---

### Post by x33a on 2009-02-21
first of all make sure you read the README file, or INSTALL file, in the archive.

assuming you have installed build-essential, these are the usual steps to compile from source.

1. ./configure
2. make
3. sudo make install.

are you following these steps? there might be different instruction depending upon the software you are trying to compile.

---

### Post by mb_webguy on 2009-02-22
A tar.gz or tar.bz is essentially the same sort of thing as a zip file.  While Linux source code is often distributed in such archives, they may contain other things.  The "configure, make, make install" sequence will only work if the archive actually contains source code and a configure file.  It may instead contain a script-based installer or a binary executable.  So you'll need to take a look at the contents in order to see what you need to do.

---

### Post by RedSingularity on 2009-02-22
Yeah i am following those steps.  What is this "build-essential" you speak of?

---

### Post by RedSingularity on 2009-02-22
> **mb_webguy said:**
> A tar.gz or tar.bz is essentially the same sort of thing as a zip file.  While Linux source code is often distributed in such archives, they may contain other things.  The "configure, make, make install" sequence will only work if the archive actually contains source code and a configure file.  It may instead contain a script-based installer or a binary executable.  So you'll need to take a look at the contents in order to see what you need to do.


How do i know what a script based installer or a binary will look like?

---

### Post by mb_webguy on 2009-02-22
From the terminal, "sudo apt-get install build-essential".

---

### Post by RedSingularity on 2009-02-22
Ok i am installing it.  What does this do?

---

### Post by mb_webguy on 2009-02-22
Well, asx33a said, there is usually a README or INSTALL file that contains instructions on what you need to do.  If not, look for a file named "configure".  If you see it, then you almost certainly have source code.  If not, look for a file ending with the file extensions "sh" (for a shell script), "pl" (for a Python script), or "bin" (for a binary executable).  If you see one of these, make it executable with "chmod u+x filename", and then run it with "./filename".

Of course, Linux doesn't really care about file extensions, so a script or executable may not necessarily have one.  If the person who wrote the software you're trying to install is halfway competent, however, you should be able to tell what you need to do fairly easily by looking at the contents of the archive -- which should contain either a text file with instructions, a well-labeled executable, or both.

---

### Post by RedSingularity on 2009-02-22
Sorry, i think we posted at the same time.  What does Build-Essential do?

---

### Post by mb_webguy on 2009-02-22
The build-essential package just gives you the tools you need to configure and install software from source code using the CMMI method.

---

