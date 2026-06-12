---
title: "[SOLVED] playonlinux 3.0.1 Python error"
date: 2008-06-05
forum: Gaming &amp; Leisure
---

### Post by Vevmesteren on 2008-06-05
hey everyone, I just installed the last version of playonlinux but when running it, the terminal throws back the following error:

```
Traceback (most recent call last):
  File "/usr/share/playonlinux/python/guiv3.py", line 25, in <module>
    lib.lng.Lang()
  File "/usr/share/playonlinux/python/lib/lng.py", line 13, in __init__
    presLan = gettext.translation("pol", Variables.playonlinux_env+"/lang/locale", languages=[locale_[0]])
  File "/usr/lib/python2.5/gettext.py", line 484, in translation
    raise IOError(ENOENT, 'No translation file found for domain', domain)
IOError: [Errno 2] No translation file found for domain: 'pol'
```


I checked that the needed additional packages are installed, and as far as I can see they are. I tried playing around with my language selection in the administration, but to no avail. So I am stomped. Any ideas anyone?

---

### Post by steve101101 on 2008-06-05
I have the same error and unsure how to fix it without running playonlinux with sudo, which i know it not a good practice.

---

### Post by steve101101 on 2008-06-05
I have the fix.

Open the terminal and type:

```

    sudo gedit /usr/share/playonlinux/python/lib/lng.py  

```
When the editor opens change this line

      locale_ = locale.getdefaultlocale () 

... to this ...

      locale_ = locale.getpreferredencoding ()

---

### Post by steve101101 on 2008-06-05
if you want to look what that file looks like or just you mine it is attached.

---

### Post by Vevmesteren on 2008-06-05
Yeah!

thank you

---

