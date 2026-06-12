---
title: "Copy all my /home to disk"
date: 2009-06-05
forum: General Help
---

### Post by luiznetto on 2009-06-05
I created a Bash shell script to copy all my files to a flash drive. It is like this:

#!/bin/bash
#This program will copy everything in this directory (except hidden files) to a chosen destination.
#But be careful! Check if the destination expressed here is the one you really mean.
cp -r 0* 1* 2* 3* 4* 5* 6* 7* 8* 9* A* B* C* D* E* F* G* H* I* J* K* L* M* N* O* P* Q* R* S* T* U* V* W* X* Y* Z* a* b* c* d* e* f* g* h* i* j* k* l* m* n* o* p* q* r* s* t* u* v* w* x* y* z* /media/disk

/media/disk being where the device is mounted, of course.

Apparently it works, in spite of some funny messages that I get like:

stat: l* no such file or directory

etc. There is only one problem, though: I'd like to make the script more general and more elegant. The device might not be mounted as /media/disk but it could be /media/disk-1, for example. Therefore, I'd like to put a variable in the place of /media/disk. But my doubt is, could a variable be an absolute file name or path? I know a variable can represent a number or character chain, but I'm unsure if a variable could represent a directory. Any help will be greatly appreciated, thanks.
Luiz

---

### Post by Ocxic on 2009-06-05
#!/bin/bash
#This program will copy everything in this directory (except hidden files) to a chosen destination.
#But be careful! Check if the destination expressed here is the one you really mean.
cp -r 0* 1* 2* 3* 4* 5* 6* 7* 8* 9* A* B* C* D* E* F* G* H* I* J* K* L* M* N* O* P* Q* R* S* T* U* V* W* X* Y* Z* a* b* c* d* e* f* g* h* i* j* k* l* m* n* o* p* q* r* s* t* u* v* w* x* y* z* $1

then  run the script like this(assuming your script is called "backup") :  "./backup /where/u/want/files" without the quotes

---

### Post by Agent ME on 2009-06-05
Why do you have all of those patterns? Just a single * will do.

Except it won't copy hidden files at all, and there's a much simpler solution - just give it the directory you want to copy:
```
cp -r . /media/disk
```
That will copy the current directory to /media/disk.
There's no reason to make this a shell script, it's just a single command.

---

### Post by iponeverything on 2009-06-05
```
cp -r 0* 1* 2* 3* 4* 5* 6* 7* 8* 9* A* B* C* D* E* F* G* H* I* J* K* L* M* N* O* P* Q* R* S* T* U* V* W* X* Y* Z* a* b* c* d* e* f* g* h* i* j* k* l* m* n* o* p* q* r* s* t* u* v* w* x* y* z* /media/disk

```

is the same as:
```
cp -r [0-9,a-z,A-Z]* /media/disk
```

you might also note that this has almost the same effect, as it does not pick up hidden files.
```
cp -r * /media/disk

```

---

### Post by Agent ME on 2009-06-05
Is it important for you to not copy any hidden files? Or just not any files hidden in the current folder? If it's the second, using "cp -r * /media/disk" will work fine.

---

### Post by dcstar on 2009-06-05
> **luiznetto said:**
> I created a Bash shell script to copy all my files to a flash drive. It is like this:
.........

Or if you just want to back up things use a tool like **unison**.

---

### Post by luiznetto on 2009-06-09
Thanks to you all, guys. I think I gained a better understanding of how this thing works. The beauty of Linux is that there is always more than one way of doing things.
Best regards to you all.):P

---

