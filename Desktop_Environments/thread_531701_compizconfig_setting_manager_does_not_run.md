---
title: "compizconfig setting manager does not run"
date: 2007-08-21
forum: Desktop Environments
---

### Post by butcher99 on 2007-08-21
I have installed compiz and it appears to work.  I can grab the spinning cube and I have 4 desktops I have hidden window buttons and the blur settings on the top of the bars but if I click on the compizconfig settings manager under system prefs nothing happens.   I uninstalled it using synaptic and reinstalled it but still no go.  

  Perhaps Compiz is not running and I am just running Emerald?

  Any suggestions?   

  Also, I can load up the emerald themes but I cannot for the life of me figure out how to actually install these.  I have clicked them, dragged them moved them but darned if I can actually install one.  

  Should I have Beryl installed as well?

   Have patience  please.. new user here to linux that is.

thanks in advance

   Running Ubunut and I have a (it appears) dreaded ATI X800 vid card 64bit version of Ubuntu

---

### Post by marcdel on 2007-08-21
I'm having the same problem. When I run ccsm in the terminal, I get:
```

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'

```

---

### Post by motin on 2007-09-03
> **marcdel said:**
> I'm having the same problem. When I run ccsm in the terminal, I get:
```

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'

```

I commented some lines out - starting on line 358 in /usr/lib/python2.5/site-packages/ccm/Window.py:
>         def CatSortCompare(self, v1, v2):
                if v1 == v2:
                        return cmp(v1, v2)
#               if self.Context.Plugins['core'].Category == v1:
#                       return cmp('', v2 or 'zzzzzzzz')
#               if self.Context.Plugins['core'].Category == v2:
#                       return cmp(v1 or 'zzzzzzz', '')
                return cmp(v1 or 'zzzzzzzz', v2 or 'zzzzzzzz')


And now it starts... EDIT: But it doesn't work since it seem not to find which plugins are enabled. A bug likely.

---

### Post by systemintheglitch on 2007-11-07
after installing sexy python, it still doesn't run.

i get the same error except for the part where it complains about python

---

### Post by K-Man_22 on 2007-11-14
I had the same error when starting ccsm after installing compiz under feisty fawn. Following [this tutorial]("http://fsb.blogage.de/article/2007/9/7/Die-beste-Art-Compiz-Fusion-auf-Ubuntu-Feisty-zu-installieren") made it work. It's written in german, but what the heck, you'll be fine - as 'update' means update and 'optional' means optional :-) Otherwise it's basically ubuntu commands.

The key is to de-installall related to compiz, beryl, and emerald, remove previously added packet sources, and then re-install as stated.

BTW: Further down on that page there is a comment by "nils (Anonym)" who posts the very same error message, shortly followed by a success notification after sticking to that tutorial. So chances are you'll be happy soon, too :-)

For a solution in English, please see [forum.compiz-fusion.org]("http://forum.compiz-fusion.org/showthread.php?t=5250&page=2").

---

### Post by virtudtierra on 2007-12-17
see:

[http://forum.compiz-fusion.org/showthread.php?p=42267#post42267](http://forum.compiz-fusion.org/showthread.php?p=42267#post42267)

:guitar:

---

