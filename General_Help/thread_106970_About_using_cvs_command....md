---
title: "About using cvs command..."
date: 2005-12-21
forum: General Help
---

### Post by equal on 2005-12-21
I'm trying to set up a theme I found a link to in this post -> [HTML]http://ubuntuforums.org/showpost.php?p=586034&postcount=3[/HTML]

The problem I'm having is when I try the first command in the list of things to do.. this happens:

```
$cvs -d:pserver:anonymous@cvs.sf.net:/cvsroot/baghira login
bash: cvs: command not found
```

Any ideas boys and girls?

---

### Post by equal on 2005-12-21
HA! Oh boy. I'm learning at least. Yes I suppose the logical first step would have been to try ```
$ sudo apt-get install cvs
```
but hey, I'm learning!

---

### Post by Freddy on 2005-12-22
You will need SVN too, for downloading the KDE admin files to the Baghira folder to be able to make a make file outta the CVS files.   /// Freddan

---

