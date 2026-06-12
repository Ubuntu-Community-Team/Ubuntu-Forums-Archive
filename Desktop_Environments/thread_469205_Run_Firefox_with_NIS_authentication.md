---
title: "Run Firefox with NIS authentication"
date: 2007-06-09
forum: Desktop Environments
---

### Post by lu98 on 2007-06-09
Hello All,

I have enabled NIS authentication on my newly installed Ubuntu 7 box and it worked fine. The problem is when I try to run Firefox 2, it starts (I can see it from ps ), but the GUI is not showing up. However, if I log in as a local user, it all works. I wonder what could be the cause.

By the way, does Firefox keep a log somewhere?

Many thanks,

---

### Post by mikedawson on 2007-06-09
Hi There,

There are a couple things to try...

I would pay attention to the firefox profile directory (under ~/.mozilla) to make sure that you have the required permissions on that.

You can also try Firefox on the command line (firefox) - which has a variety of options - including -jsconsole which should try to just open the error console to give you some ideas about what's going on.

Hope that helps a little..

-Mike

---

### Post by donatell0 on 2008-01-16
I also have this problem. What is happening that firefox is taking really long to start up. More than an hour or so. I have permissions for the .mozilla folder (read, write and execute).

firefox -jconsole also does not produce any output for a long time.

Any help is most welcome.

---

