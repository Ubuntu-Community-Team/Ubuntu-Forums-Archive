---
title: "Open office does not use the default window manager after reinstal"
date: 2009-03-02
forum: General Help
---

### Post by jARLAXL on 2009-03-02
I installed Openoffice 3 but decided to go back to 2.4. The question is, how to make openoffice to get the default settings of appearance that all other applications have? In other words currently OO windows look like the one in the bad.png (grey), while i want to make them look like the one in the good.png (brown)

Thanks a lot

---

### Post by jARLAXL on 2009-03-03
Bump

---

### Post by Tibuda on 2009-03-03
OpenOffice is not really a GTK+ application, so it's not fully integrated into the system.

---

### Post by jARLAXL on 2009-03-03
> **danielrmt said:**
> OpenOffice is not really a GTK+ application, so it's not fully integrated into the system.

Yes i can see that.
The question is how to integrate it as it was before i install the OO 3.:confused:
Or do i have to reinstall Ubuntu to get it? Is that the only way?

---

### Post by SamNSane on 2009-03-03
> **jARLAXL said:**
> Yes i can see that.
The question is how to integrate it as it was before i install the OO 3.:confused:
Or do i have to reinstall Ubuntu to get it? Is that the only way?

I know what you mean. Here's something weird for us to consider. I have two systems side-by-side on my desktop right now, a notebook and a desktop -- both running Ubuntu 8.04. They have similar, but not identical, installation histories. Both have OpenOffice 3 from the Open Office Scribblers launchpad ppa repository.

On the desktop I get the nice nautilus-like open/save dialog. On the notebook I get the much less efficient and ugly open/save dialog as in your second example. I've studied the Tools/Options settings on both systems and tried making changes until I'm blue in the face. None of my fiddling has managed to get me the pretty open/save dialog on the notebook.

---

### Post by SamNSane on 2009-03-03
I just found an answer. I compared the list of packages containing "gtk" that were installed on my two systems. The desktop had one package -- openoffice.org-gtk -- which was not installed on the notebook. Once I installed that package from synaptic on the notebook, the open/save file dialog (and other behaviors) in Open Office 3 suddenly got prettier!

If you installed OpenOffice 3 by some means other than using a repository, I'm not sure how you'll go about getting that package and installing it for use with your OpenOffice installation.

---

### Post by jARLAXL on 2009-03-03
SamNSane you are wonderful! 
Thats exactly what i was looking for.
Thanks a lot lot lot.

---

### Post by SamNSane on 2009-03-03
I should thank you. Your question encouraged me to find out why I was seeing  those ugly dialogs. Now OpenOffice is pretty on my notebook!

Have a good day!

---

