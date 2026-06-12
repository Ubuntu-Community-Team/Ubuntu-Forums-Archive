---
title: "Change icon for all files of a certain type?"
date: 2009-03-12
forum: Desktop Environments
---

### Post by Mothinator on 2009-03-12
I installed mathematica 7.0 and it registered itself to open all *.m files and changed their icons to the mathematica logo.

The problem is most of my *.m files are MATLAB source code. 

I've figured out how to get all the files to open with gedit by default, but how do you change all of their icons back?

By the way, all the *.m files show as MIME type "application/mathematica" whereas they used to show as "text/plain."


Any help would be appreciated!

---

### Post by ad_267 on 2009-03-12
You can do this with assogiate, which is available in the repositories.

---

### Post by Mothinator on 2009-03-12
Thanks for the tip on assogiate.


It looks like it should do the job, but one problem: It won't let me remove filetypes.

As in I can see *.m in the filename pattern area, but removed is greyed out. It seems I can only remove patterns that I add myself.

I've also tried it with sudo.

Any ideas?

---

### Post by Mothinator on 2009-03-13
I never did find out how to get assogiate to remove file extension from MIME types.

But here is the solution from Mathematica tech support:

> xdg-mime uninstall --mode system /usr/local/Wolfram/Mathematica/7.0/SystemFiles/Installation/Wolfram-Mathematica.xml



Then log out and log back in

---

### Post by ad_267 on 2009-03-13
Thanks for posting your solution, hopefully that will help anyone else having this problem. 
I guess assogiate can only change user preferences and not the system wide file associations.

---

