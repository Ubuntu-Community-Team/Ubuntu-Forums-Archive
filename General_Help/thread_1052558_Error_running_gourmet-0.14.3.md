---
title: "Error running gourmet-0.14.3"
date: 2009-01-27
forum: General Help
---

### Post by natibo on 2009-01-27
I installed this program using the setup.py command. Now when I run it I get the following error:

[INDENT]Traceback (most recent call last):
  File "/usr/bin/gourmet", line 13, in <module>
    from gourmet.OptionParser import *
  File "/usr/lib/python2.5/site-packages/gourmet/__init__.py", line 14, in <module>
    import keymanager
  File "/usr/lib/python2.5/site-packages/gourmet/keymanager.py", line 3, in <module>
    from defaults import langProperties as langProperties
ImportError: cannot import name langProperties
[/INDENT]

I tried removing and reinstalling the old version from the repository but it didn't work.

Any help is appreciated.

---

### Post by Partyboi2 on 2009-01-29
What happens when you try installing the one in the ubuntu repos?
Another thing you could try is downloading the deb from [[COLOR=Blue]here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=108118&package_id=159597&release_id=656902")

---

### Post by Fenixin on 2009-04-08
The solution is here:

[http://sourceforge.net/forum/forum.php?thread_id=2932910&forum_id=371768]("http://sourceforge.net/forum/forum.php?thread_id=2932910&forum_id=371768")

It worked for me.

---

