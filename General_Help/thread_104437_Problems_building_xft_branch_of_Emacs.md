---
title: "Problems building xft branch of Emacs"
date: 2005-12-16
forum: General Help
---

### Post by hannu on 2005-12-16
Hi,

As a long-time Mac user I've been spoiled by all sorts of superfluous eye candy, so I thought I'd try to compile the recent XFT branch of CVS Emacs that supports antialiased fonts. I got the code from Miles Bader's GnuArch repository as per [http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs]("http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs"),
and attempted to compile it. However, it appears something goes wrong with leim: "sudo make bootstrap" produces

[INDENT]> if [ x`(cd /home/hannu/emacs--xft-jhd--0--patch-1/leim && /bin/pwd)` = x`(/bin/pwd)` ] ; then \
  EMACSLOADPATH=/home/hannu/emacs--xft-jhd--0--patch-1/leim/../lisp ../src/emacs -batch --no-init-file --no-site-file --multibyte -l /home/hannu/emacs--xft-jhd--0--patch-1/leim/../lisp/international/quail \
    --eval "(update-leim-list-file \".\")" ; \
else \
  EMACSLOADPATH=/home/hannu/emacs--xft-jhd--0--patch-1/leim/../lisp ../src/emacs -batch --no-init-file --no-site-file --multibyte -l /home/hannu/emacs--xft-jhd--0--patch-1/leim/../lisp/international/quail \
    --eval "(update-leim-list-file \".\" \"/home/hannu/emacs--xft-jhd--0--patch-1/leim\")" ; \
fi
Updating /home/hannu/emacs--xft-jhd--0--patch-1/leim/leim-list.el ...
Loading vc-arch...
Wrong type argument: number-or-marker-p, nil
make[2]: *** [leim-list.el] Error 255
make[2]: Leaving directory `/home/hannu/emacs--xft-jhd--0--patch-1/leim'
make[1]: *** [leim] Error 2
make[1]: Leaving directory `/home/hannu/emacs--xft-jhd--0--patch-1'
make: *** [bootstrap-build] Error 2[/INDENT]

I'm mystified and eyecandy-deficient. Any ideas and comments would be much appreciated.

---

