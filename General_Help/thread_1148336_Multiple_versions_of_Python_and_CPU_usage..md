---
title: "Multiple versions of Python and CPU usage."
date: 2009-05-04
forum: General Help
---

### Post by lovinglinux on 2009-05-04
I want to understand how multiple versions of Python works on the same machine. 

Here is the situation:

I'm didn't notice overall speed improvements after installing Jaunty and I'm experiencing problems with Flash, related to high CPU usage. I did a clean install but installed all my favorite software from Hardy, using *dpkg --set-selections*. 

So after reading a thread about Deluge CPU usage being related to Python 2.5, I decided to remove it, along with *guake*, *mimms* and *ontv*, which still depend on it.

It seems that the system is more responsive now, the CPU usage has dropped considerably and I'm able to play Flash videos without freezing Firefox. Still stutters sometimes, but is definitely watchable.

So how does this thing works? I have for example several python scripts running in the background (screenlets). They all work with Python 2.6, but is it possible that since I had Python 2.5 that they could be using it instead of the newest version? Or can different versions of Python be loaded at the same time?

I did notice that Synaptic change the association of the installed programs from Python 2.5 to Python 2.6. Is it possible to change this manually?

---

