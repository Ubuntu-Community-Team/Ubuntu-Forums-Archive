---
title: "GCompris will not load"
date: 2010-02-27
forum: Education &amp; Science
---

### Post by Chris_cur on 2010-02-27
Hello everyone.

I just installed the Edubuntu preschool suite and I cannot get GCompris to load. I have regular Ubuntu Jaunty.

I click on it, I get the [loading circle] and shows up as Loading down at the bottom of the screen with the other programs that are running. Then it just disappears and nothing shows up.

I am also having issues with Linux Letters and Numbers.  The lettre "a" and "b" flashcards open up a picture real fast and then the whole program closes.

Any advice on these two? I am trying to get these loaded up for my 3.5 yr old son.

---

### Post by jbrefort on 2010-03-01
Try starting GCompris from a terminal to get any useful error or warning message (you might also examine .xsession-errors for the same messages).

---

### Post by Chris_cur on 2010-03-01
Merci,

I get the following..
```
$ gcompris
exec_prefix NULL
XF86VidMode: Compiled with XF86VidMode.
If you have problems starting GCompris in fullscreen, try the -x option to disable XF86VidMode.

** (process:8128): WARNING **: Binary relocation disabled
package_data_dir         = /usr/share/gcompris/boards
package_locale_dir       = /usr/share/locale
package_plugin_dir       = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
Infos:
   Config dir '/home/cur/.config/gcompris'
   Users dir '/home/cur/My GCompris'
   Database '/home/cur/.config/gcompris/gcompris_sqlite.db'
Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted

```

---

### Post by jbrefort on 2010-03-02
> **Chris_cur said:**
> 
Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted
[/CODE]

The Numeric module seems missing, might be in the python-numpy package, but I'm not an expert.

---

### Post by Chris_cur on 2010-03-02
> **jbrefort said:**
> The Numeric module seems missing, might be in the python-numpy package, but I'm not an expert.

ou est le python package? probablement il y a un autre thread pour cette problem?

merci

---

