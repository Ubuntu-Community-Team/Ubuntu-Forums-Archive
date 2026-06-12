---
title: "Problem with Emacs (on the console/ Terminal)"
date: 2009-08-16
forum: Desktop Environments
---

### Post by hictio on 2009-08-16
I have Emacs (emacs-nox) installed on my Jaunty ever since I have made install on top of Intrepid (a clean one), no problems at all, all the hardware on my Compaq F700 works, etc, etc, etc.

Now, I have noticed that Emacs it is printing an error message every time I start it:

```

Cannot open load file: encoded-kb

```

It starts Ok, but it doesn't load my ~/.emacs file, tried blanking it or not using any ~/.emacs file at all, but it still prints it.

I'm running:

```

~$ emacs --version
GNU Emacs 22.2.1
Copyright (C) 2008 Free Software Foundation, Inc.
GNU Emacs comes with ABSOLUTELY NO WARRANTY.
You may redistribute copies of Emacs
under the terms of the GNU General Public License.
For more information about these matters, see the file named COPYING.

```

This is what I have installed regarding Emacs:

```

~$ dpkg -l | egrep emacs
ii  emacs22-bin-common                         22.2-0ubuntu2                        The GNU Emacs editor's shared, architecture 
ii  emacs22-common                             22.2-0ubuntu2                        The GNU Emacs editor's common infrastructure
ii  emacs22-nox                                22.2-0ubuntu2                        The GNU Emacs editor (without X support)
ii  emacsen-common                             1.4.17                               Common facilities for all emacsen

```

My ~/.emacs it is pretty basic, [here](http://oesediez.blogspot.com/2008/01/oh-emacs-my-emacs.html) is a copy of it.

This problem it is fairly recent, I have noticed this today, and it is happening on both a Gnome Terminal on X Window, and on the plain console without X.

---

### Post by tripleee on 2009-08-18
Reported at [https://bugs.launchpad.net/bugs/415186](https://bugs.launchpad.net/bugs/415186) -- following up there.

---

