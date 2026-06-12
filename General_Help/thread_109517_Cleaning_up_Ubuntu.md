---
title: "Cleaning up Ubuntu"
date: 2005-12-28
forum: General Help
---

### Post by avox on 2005-12-28
I'm still new to Ubuntu so I've been trying tons of apps to see what works best for me, but I'm finding that after I uninstall something, its dependencies are still installed.  #-o   So, rather than go through and make a list of every one I need to remove come uninstall time, does anybody know a safe and easy command, app, etc. that cleans up (finds and uninstalls, specifically) packages that aren't needed by any programs anymore?  

I'm wary of going around and deleting stuff since I'm not up to snuff on fixing a linux install yet.  :?  Is it safe to just get rid of any references left by these programs, such as their hidden folders in my home directory?  Any other tips pertaining to keeping Ubuntu environmentally friendly would be helpful as well.

---

### Post by GameGod on 2005-12-28
I think [GTKOrphan]("http://www.marzocca.net/linux/gtkorphan.html") is what you're looking for. :)

(But be careful you don't pooch something important...)

---

### Post by glacierre on 2005-12-28
Yes it's a frontend for deborphan. 

I suggest running it a couple of times since sometimes the freshly removed non-used-packages free another ones.

Previously use aptitude/synaptic to navigate through installed packages (use advanced view and a filter in synaptic to view only installed) and their description, so you can discover many that you don't need at all.

---

### Post by avox on 2005-12-28
Trying it out now.

NIIIIICE.  With my trigger finger, I do believe it's time to fubar me some ubuntu.  :twisted: 

Thanks for the head's up, y'all.

---

### Post by limit223 on 2005-12-28
Another tool still in day by day development would be kleansweep

---

### Post by avox on 2005-12-28
another interesting possibility, thanks.  methinks i should be making a list somewhere.

---

