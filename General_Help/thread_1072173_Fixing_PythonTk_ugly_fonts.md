---
title: "Fixing Python/Tk ugly fonts?"
date: 2009-02-17
forum: General Help
---

### Post by Yako no Kai on 2009-02-17
I wrote an application in python to help myself look up kanji (Japanese characters). In Windows it looks fine, but in Ubuntu the text looks blocky and illegible (see [_sample image_](http://sites.google.com/site/jeremylakatos/Home/senkazuKanjiDictionary/senkazunotes/senkazulin01.png?attredirects=0)).  This makes the application pretty useless.

In other applications, such as leafpad, kanji fonts look fine after following the steps in this post: [http://ubuntuforums.org/showthread.php?t=812552](http://ubuntuforums.org/showthread.php?t=812552).  Just not in Tkinter (aka python-tk).

From what I have been able to determine, it seems that I need to either compile python myself or wait for python 2.6 (with Tk 8.5) to show up in the repos.  My two questions are these:

Is this actually true, or have I gotten confused by a related issue that doesn't truly apply?

Is there any workaround to get fonts looking decent, outside compiling python myself? 

Here is a little bit of test code that displays kanji. It looks fine in Windows but awful in Ubuntu:
```

from Tkinter import *
root = Tk()
Label(root, font = ('MS PMincho', 40), text=u'\u7DDA').pack()
root.mainloop()

```

---

