---
title: "OpenSceneGraph"
date: 2009-02-03
forum: General Help
---

### Post by fhslacrosse13 on 2009-02-03
I'm trying to install OSG from source, but am have difficulties with the whole process.
I followed the step laid out here: [http://www.opendimension.org/ida5D/compile.php](http://www.opendimension.org/ida5D/compile.php)
I'm not sure if I did the last part correctly
```
Then make some settings:
export PATH=${PATH}:/usr/local/share/OpenSceneGraph/bin

export OSG_FILE_PATH=/WHEREDIDYOUEXTRACTDATAFILES/OpenSceneGraph-Data

export LD_LIBRARY_PATH=/usr/local/lib
```

When I type "osgviewer cow.osg" into terminal I get this message:
```
user@user-desktop:~$ osgviewer cow.osg
osgviewer: error while loading shared libraries: libOpenThreads.so.11: cannot open shared object file: No such file or directory

```

I've got the source located in:  "/home/user/programs/OpenSceneGraph"
and the build_OSG in:  /home/user/programs/build_OSG

Everything seemed to install correctly according to the link, but then again probably no considering it doesn't work

I've also tried osgversion with the same message.

---

### Post by fhslacrosse13 on 2009-02-04
I think my problem has something to do with linking the files to the system path, but I'm not completely sure.  Don't want to try something without knowing ahead of time. 

Hopefully someone has some feedback.  That was a suggestion from the PhD. student I'm working with.

---

### Post by fhslacrosse13 on 2009-02-05
No one here ever have the same problem?

---

### Post by lognok on 2009-03-21
See this forum thread: [http://ubuntuforums.org/showthread.php?t=479296&highlight=openscenegraph](http://ubuntuforums.org/showthread.php?t=479296&highlight=openscenegraph)

---

