---
title: "Problem with package php-mode"
date: 2006-02-23
forum: Desktop Environments
---

### Post by mority on 2006-02-23
Hello Board,

I have a problem with the package php-mode which adds PHP syntax highlighting to emacs. When I installed the package with synaptic I got the following error from synaptic:
```
E: php-mode: subprocess post-installation script returned error exit status 1
```
and the apt-get output looked similar to the following (just the lines regarding php-mode package):
```

Preconfiguring packages ...
Selecting previously deselected package nano-tiny.
(Reading database ... 62272 files and directories currently installed.)
Unpacking nano-tiny (from .../nano-tiny_1.3.8-2_i386.deb) ...
Setting up php-mode (0.1-1) ...
install/php-mode: Handling install for emacsen flavor emacs21
Wrote /usr/share/emacs21/site-lisp/php-mode/php3-mode.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/php-mode/php-mode.el:
  !! Wrong type argument ((stringp nil))
Done
emacs-package-install: /usr/lib/emacsen-common/packages/install/php-mode emacs21 emacs21 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing php-mode (--configure):
 subprocess post-installation script returned error exit status 1
Setting up nano-tiny (1.3.8-2) ...

Errors were encountered while processing:
 php-mode
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

After that, the package gets displayed as installed and surprisingly it works fine in emacs. So I thought: forget about the error messages, at least it works.
But the problem is, everytime I want to install any package, apt-get is trying to reconfigure the php-mode package and throws the error messages again which is pretty annoying. You can see that in the output above as I was just installing nano-tiny package in this case.

Does anyone has an idea how to fix this?

---

### Post by speeves on 2006-11-21
The quick fix is to:

sudo dpkg --purge php-mode

as apt-get remove php-mode errors out as well, and doesn't remove the package...

---

