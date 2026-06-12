---
title: "Some software not working?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by ultra.nj on 2005-10-26
I've been using Hoary for a few weeks, and recently upgraded to Breezy.  There's one weird problem where it doesn't allow me to open up the Synaptec manager.  I click on it and nothing happens, anyone know what the problem is?

---

### Post by NewWithoutClue on 2005-10-26
well you could try re-installing synaptic...
open a a terminal and enter the following..
( you need to be root, or use sudo )
'apt-get remove synaptic'
then after that
'apt-get install synaptic'
;)
Regards,
Paul.

---

### Post by ultra.nj on 2005-10-26
I try that and it says

```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 permission denied)
E: Unable to lock the list directory

```

I also have some other problems..

When I first log in, I get an error message that says 
```
Could not look up internet address for ubuntu.  This will prevent GNOME from operating correctly.  It may be possible to cerrct the problem by adding ubuntu to the file /etc/hosts.
```

And another problem is that I can't use sudo, it says
```
unable to lookup ubtunu via gethostbyname()
```

---

### Post by RAOF on 2005-10-26
Try [here]("http://www.ubuntuforums.org/showthread.php?t=81561&highlight=sudo+hostname").  This looks like the same problem.

---

