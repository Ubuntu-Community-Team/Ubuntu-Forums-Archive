---
title: "mayavi2 appears to install incorrectly"
date: 2008-06-08
forum: Education &amp; Science
---

### Post by gus_393 on 2008-06-08
I`m getting the error

  File "/usr/lib/python2.5/site-packages/enthought/traits/trait_notifiers.py", line 428, in rebind_call_1
    self.dispatch( getattr( self.object(), self.name ), new )
  File "/usr/lib/python2.5/site-packages/enthought/traits/trait_notifiers.py", line 373, in dispatch
    handler( *args )
  File "/usr/lib/python2.5/site-packages/enthought/mayavi/app.py", line 173, in _start
    self.script = app.get_service(IMAYAVI)
  File "/usr/lib/python2.5/site-packages/enthought/envisage/core/application.py", line 654, in get_service
    raise SystemError("Service %s not found" % str(interface))
Exception: Service enthought.mayavi.IMayaVi not found


Then I the "Frame Based Inspector" pops up and tells me there has been an error.

Is anyone else getting this or know what I might be doing wrong?...i just tried to install the mayavi2 package in synaptic.

Thanks in advance.

---

### Post by joekilner on 2008-06-19
I'm getting this too.

---

### Post by os.getlogin on 2008-07-15
any update on this?  I get it too

---

### Post by Friqenstein on 2008-07-15
Mine 'appears' to have installed ok, but doesn't run correctly. Trying to render or even load a .vtk files just makes my screen go grey.

---

### Post by os.getlogin on 2008-07-16
> **Friqenstein said:**
> Mine 'appears' to have installed ok, but doesn't run correctly. Trying to render or even load a .vtk files just makes my screen go grey.

Yeah, mayavi2 "runs" for me in the sense that it starts up, but I can't load any data.  I still get enthought.* errors during any update though.  Something's amiss.

---

### Post by WW on 2008-07-16
According to the [mayavi2 listing](http://packages.ubuntu.com/hardy/mayavi2) at packages.ubuntu.com, mayavi2 is packaged by the "Ubuntu MOTU Developers".  You could send an email to them, or try reporting a bug (see the links in that page).

You could also try the [enthought-dev mailing list](https://mail.enthought.com/mailman/listinfo/enthought-dev).  I don't know if enthought is directly involved in building the Ubuntu packages, but they probably know who is, and the packagers might keep an eye on that mailing list.

---

