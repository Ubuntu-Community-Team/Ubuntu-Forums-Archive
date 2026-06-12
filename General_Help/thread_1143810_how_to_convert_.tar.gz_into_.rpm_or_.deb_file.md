---
title: "how to convert .tar.gz into .rpm or .deb file"
date: 2009-04-30
forum: General Help
---

### Post by mubbashar on 2009-04-30
please tell me how to convert .tar.gz into .rpm or .deb file??????????

---

### Post by benj1 on 2009-04-30
if its for something you want to install you don't, extract the file and open it up it should have an INSTALL and/or README file that will tell you how to install it, probably to type in the terminal
```
./configure
```

```
make
```

```
sudo make install
```

---

### Post by mubbashar on 2009-04-30
how can i install it using gui not terminal

---

### Post by unutbu on 2009-04-30
To make a .deb instead of directly installing the package, use could use checkinstall:

```
./configure
make
sudo apt-get install checkinstall
sudo checkinstall -D --fstrans=no make install
```

There is no GUI way to do this as far as I know.

mubbashar: Do you know what is inside the tar.gz? Does it contain source code that need to be compiled, or is it just a collection of files that need to be extracted? The above instructions are for the first case (compiling), not the second (extracting).

---

### Post by mubbashar on 2009-04-30
you are sure or not

---

### Post by benj1 on 2009-04-30
if its a program that you have downloaded, have you looked on synaptic to see if its there?

if not extract it (right click and extract)
if the instructions are the same as i assumed previously go into a terminal
and assuming the file is on your desktop type
```
cd ~/Desktop/*extracted_file*
```
then follow the steps above.
if the instructions are different post the post the instructions and we may be able to help

---

### Post by mubbashar on 2009-04-30
when i want to install maximum time i got some errror

---

### Post by Kareeser on 2009-04-30
> **mubbashar said:**
> how can i install it using gui not terminal

If this is the source code of a program, you can't do it through the GUI (as far as I know).

Try the synaptic package manager first. Your program may already be in the repositories.

---

### Post by mubbashar on 2009-04-30
but there are many programs which are not in repository.

---

### Post by snowpine on 2009-04-30
A tar.gz file is just an archive file, like .zip in windows. Anything could be inside it. You can extract the files within using any Archive Manager application. Typically you would look for a README file, or follow instructions from the website where you got it.

---

### Post by Simian Man on 2009-04-30
You are not giving very much info.  What are you trying to install?  What files are in the tarball?  What does the README or INSTALL file say (if there is one)?  Is there a file called Makefile or makefile?

Believe it or not there is no standard way to install tarballs or convert them into rpm or deb - and there certainly isn't a way to do it with the GUI.  People will help you, but you must give more detailed info.

---

