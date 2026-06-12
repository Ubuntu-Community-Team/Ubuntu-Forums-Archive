---
title: "Problems with Open Office"
date: 2008-09-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vas72985 on 2008-09-11
I just got a new Dell preloaded with Ubuntu (8.04). Previously I dual booted on a Dell with Ubuntu and Windows XP and everything worked fine, but alas, my computer was getting on in years and it was time for a new one.

My problem involves getting Open Office to open, in that, I can't...When I try to open any of the Open Office Programs I get the following error:

"The application cannot be started. OpenOffice.org user installation could not be processed due to missing access rights. Please make sure that you have sufficient access rights for the following location and restart OpenOffice.org:

/home/vincent/.openoffice.org2 "

I'm a very strict beginner, so I would appreciate any and all help you can give me with this problem. I have uninstalled and reinstalled Open Office and that didn't change anything. Thanks in advance.

---

### Post by vas72985 on 2008-09-11
I also notice that when I go to the folder it tells me I don't have access to, the .openoffice.org2 folder has a little locked symbol next to it, and when I right click and choose Properties and then the Permissions tab, it says the owner is "root" and at the bottom it says "You are not the owner, so you can't change these permissions"

---

### Post by ad_267 on 2008-09-11
To fix this you can go to Applications - Accessories - Terminal and enter:
```
sudo chown -R vincent:vincent /home/vincent/.openoffice.org2
```
Then you will just need to enter your password.

It's weird for that to happen unless you accidentally did it yourself somehow.

---

### Post by vas72985 on 2008-09-11
that worked; thanks a lot. I actually stumbled on the chown command right before I saw your reply. At least I was on the right track. I wonder how it got changed to root... Thanks again!

---

### Post by ad_267 on 2008-09-11
That's good it worked. If you prefer to stay away from the terminal you can also press Alt-F2 and run "gksu nautilus" and then you will get a file browser with root access to the whole file system. Sometimes it's handy to make a shortcut to run this.

---

