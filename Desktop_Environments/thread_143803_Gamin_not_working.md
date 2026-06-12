---
title: "Gamin not working?"
date: 2006-03-13
forum: Desktop Environments
---

### Post by Kray on 2006-03-13
It looks that gamin (app/service which purpose is monitoring file) isn't (or stopped) working properly on my Ubuntu Breezy. If I open some folder in Nautilus, then launch gedit and save new document in this directory Nautilus isn't notified about changes. I need to hit 'Refresh' button to make Nautilus aware of freshly created file.
	
I'm not sure if it wasn't working at all or maybe this is result of some changes in settings. Any ideas?

---

### Post by stoeptegel on 2006-03-14
I don't know about a solution, but i do know that some of us have high CPU by this process, and i myself have a huge memory leak (reported [here](https://launchpad.net/distros/ubuntu/+source/gamin/+bug/34699))

So there's something seriously wrong with this package. Lets hope they fix this soon.

---

