---
title: "My lower-case &quot;c&quot; key is broke, but only in terminal..."
date: 2015-12-27
forum: Desktop Environments
---

### Post by Felix_Ryan on 2015-12-27
Hey all,

I consider myself a "not newb" if you will, but I have always taken my keyboard entry for granted.  Realised today that in terminal my lower case "c" doesn't work.

To be clear:
- Only ever experience this problem in terminal, i.e. it works perfectly in other applications such as Firefox (which I am using to post this thread "ccCCccCCccc")
- Upper case "C" works fine both when used with "Shift" and "Caps Lock"
- Crtl C works fine
- Sift Ctrl C (and associated V) work fine as well.

Clearly this isn't a physical fault, but I just have no idea how to go about working out what the problem is, let alone fixing it!  Any hints gratefully received!

For the record I am using Ubuntu 15.10 and it was installed only a few days ago.

Thanks in advance!

Felix

Just as an interesting extra piece of information...

I thought it would be a good idea to use gedit to write my commands and then copy/paste them into terminal.  Unfortunately it pastes all chars except the "c".

Hopefully this will make sense to someone!

Just realised more detail that I needed to include:

Persistent over reboots.
No amount of trying keyboard shortcuts seem to release this problem
Tab completion works correctly if there is a "c" in the filename etc.

---

### Post by oldos2er on 2015-12-27
Are you using gnome-terminal (I forget which is the default)? Have you tried xterm or a different terminal?

---

### Post by matt_symes on 2015-12-27
Hi

Have you edited your *readline* configuration file (~/.inputrc) in any way ?

Kind regards

---

### Post by steeldriver on 2015-12-27
^^ my thoughts exactly? what is the output of

```

bind -p | grep $'\x63\"'

```

(the funny $'\x63\"' part is just a way to grep for a lower case c without typing 'c')

---

### Post by Felix_Ryan on 2015-12-27
Guys - thank you very VERY much!

I had edited my /etc/inputrc... and mis-typed:

set completion-ignore-case On

I fixed it and now it works perfectly!

Thank you!!

---

### Post by coldraven on 2015-12-27
> - Sift Ctrl C (and associated V) work fine as well.
Your h key is also not working :) Merry Christmas!

---

