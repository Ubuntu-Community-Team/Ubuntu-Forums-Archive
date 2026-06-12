---
title: "Kile forward search"
date: 2005-11-12
forum: Desktop Environments
---

### Post by RdJ on 2005-11-12
Hi all,

I cannot get Kile forward search to work in Ubuntu. I have googled for days about this, but nothing seems to work and little information is available, and I desperately need some hints, because I find myself booting Windows now. In some instances, I can get the viewer to display the "target" line number in the lower right-hand corner of the editor, but the editor refuses to jump to the correct location. The Kile handbook seems to presume it all "just works" after specifying "modern" instead of "default" among the build options.

The inverse search works, both for the built-in viewer and KDVI. The only issue is forward search.

Anjuta doesn't display correctly either. Do I perhaps have some display package that is faulty?

Any suggestion will be appreciated.

RdJ

---

### Post by jetpeach on 2006-06-13
Not sure this will fix your problem (or you've probably had it fixed by now) but I posted what might work for you in this thread
[http://ubuntuforums.org/showthread.php?t=179581&page=2&highlight=kile+inverse](http://ubuntuforums.org/showthread.php?t=179581&page=2&highlight=kile+inverse) EDIT: I lied, I was going to post there but that thread is closed.  Anyway, solution is below, at least what worked for me.

Basically, I did Settings->Configure Kile->Build Tab->Select latex->change options to " -interaction=nonstopmode --src-specials '%source'  "
When I do forward search it works now, but I have to select ForwardDVI under Build->View

---

### Post by drini on 2008-04-24
The problem is a faulty command line used by Kile.
Go Settings , Tools, select LateX and change that to

-interaction=nonstopmode -src ‘%source’

It's documented on 
[http://drini.wordpress.com/2008/04/25/busqueda-inversa-kile-kdvi/](http://drini.wordpress.com/2008/04/25/busqueda-inversa-kile-kdvi/)
which is in spanish, although the command line needing fixed is clear from the post

---

