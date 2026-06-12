---
title: "Matlab crashes after splash screen (already tried export command..)"
date: 2010-02-03
forum: Education &amp; Science
---

### Post by warrd on 2010-02-03
Hi there.

I recently had to reinstall my operating system from scratch.

I have the latest version of Matlab (r2009b) which was working fine before, but after reinstalling it on Ubuntu 9.10, it does not work.

When I run from the terminal, the splash screen appears for a few seconds then disappears, giving the following message:

> Unable to initialize com.mathworks.mwswing.MJStartup
Fatal Error on startup: Failure loading desktop class

I know others have had similar problems, and have tried the advice suggesting to add these lines to the start-up script:

> export AWT_TOOLKIT=MToolkit
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/

This has not fixed it.

Anyone got any ideas?

Thanks

---

### Post by warrd on 2010-02-04
Just to let you know I seem to have got it working for the time being.

I commented out the line 

> export AWT_TOOLKIT=MToolkit

and restarted and it now seems to work!

---

