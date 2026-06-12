---
title: "Where to install programs?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Daboo on 2005-11-03
I was having problems with getting eclipse using synaptic, so i d/led it manually. Now I just uncompressed it to /usr/share and it works fine. Is this the best place for it?

---

### Post by aysiu on 2005-11-03
[QUOTE=Daboo]I was having problems with getting eclipse using synaptic, so i d/led it manually. Now I just uncompressed it to /usr/share and it works fine. Is this the best place for it?[/QUOTE] I usually pop stuff into /usr/local/bin and then make a sim-link from there to /usr/bin

---

### Post by Daboo on 2005-11-03
So extract to /usr/local/bin and then point to it from /usr/bin? Sorry, I'm new to links and stuff.

---

### Post by SilentCacophony on 2005-11-03
if you enter:
```
echo $PATH
```
you should see what your path setup is; for instance the default setup should look as so:
```
brian@ubuntu:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

```
Any of those entries will be suitable to place a program in. Note that usr/local/bin is the first place the system looks, so that should be fine without linking to anywhere else.

---

### Post by Daboo on 2005-11-03
I'm confused, so the entire eclipse folder should go under /usr/local/bin?

---

### Post by SilentCacophony on 2005-11-03
> I'm confused, so the entire eclipse folder should go under /usr/local/bin?

No, the executable file (or a link to it, as aysiu mentioned) should be in one of the folders in the $PATH. If the executable is hidden in a subfolder, it won't be found.

So, you may either move the executable into the $PATH, or dump the folder wherever you like, then symlink to the executable from within the $PATH.

to make a symlink, you can use the commandline easily:

```
sudo ln -sf /usr/local/bin/*name_of_program* *<path_to_program>*
```

that would make a symlink named *name_of_program* in the usr/local/bin folder, which points to the actual program located at *<path_to_program>*. You need to identify the actual executable file first, of course.

You can run this to see a bunch of examples of links on your system:

```
ls -la /etc/alternatives
```

---

### Post by aysiu on 2005-11-03
Yeah, I'm sorry I wasn't clearer about that before.
The sim-link is just for the executable, not for the whole folder.
And you can do it graphically (with ```
gksudo nautilus
```) by just dragging (I think a right-click or middle-click drag) the executable from /usr/local/bin/programname/executablename to /usr/bin/executablename and selecting "link here" or "create link."

---

### Post by FLeiXiuS on 2005-11-03
[QUOTE=aysiu]I usually pop stuff into /usr/local/bin and then make a sim-link from there to /usr/bin[/QUOTE]

There shouldn't be a need to do a symbolic link from /usr/local/bin -> /usr/bin for the most part, $PATH should have included /usr/local/bin as an executable path location.

Woops, I didn't read the post ahead..this was already mentioned!  Clumbsy ME!

---

### Post by aysiu on 2005-11-03
Well, you learn something new every day... or at least I do. Thanks for the tip.

---

### Post by Daboo on 2005-11-03
Ok, one more thing. So in /usr/bin there is a sym link, 'gimp' which points to the gimp2.2 executable which is also in /usr/bin. K, makes sense. But where is the program data for gimp stored? And how does it know where that is when you run gimp?

Based on this I'm wondering where I should toss my eclipse folder as to not clutter things up. Thanks for the help so far!

---

### Post by Daboo on 2005-11-03
Aha:

bin	Most user commands
include	Header files included by C programs
lib	Libraries
local	Local hierarchy (empty after main installation)
sbin	Non-vital system binaries
share	Architecture-independent data

Since eclipse I downloaded is precompiled, should I just toss it in /opt and put a sym link from /usr/bin?

---

### Post by Daboo on 2005-11-04
Crap, i have a symlink, but if I try to run eclipse from anywhere but where i installed it, i get "Unable to access jarfile startup.jar"

---

### Post by Daboo on 2005-11-04
anyone?

---

### Post by binarymelon on 2005-11-04
A good place to throw it is in /opt.  Then just create a symlink, to the executable.  I think this will work, but no guarantees, because Java can be a pain in the arse.

Edit:
Sorry, didn't read those last two posts.  Try creating a small shell script called eclipse in /usr/bin that executes the /opt/eclipse/eclipse (I believe that is the executable) directly.

---

