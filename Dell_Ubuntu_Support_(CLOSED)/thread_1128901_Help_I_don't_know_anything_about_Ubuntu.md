---
title: "Help I don't know anything about Ubuntu"
date: 2009-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gonzalesamy on 2009-04-18
[INDENT][/INDENT]My son's grandmother bought him this system and I am not familiar with anything.  It was in the middle of a software udate and then shut down....which caused it not to download all the necessary files.  Now it is giving me an error (E: dpkg was interrupted. you must manually run 'dpkg --configure -a' to correct the problem.  

E: _cache->open()failed. please report.

Please help it will not allow me to pull up a terminal to manually configure.

Also it will not allow me to connect to wireless but I can get online via network cable.

---

### Post by lisati on 2009-04-18
Open up Accessories->Terminal on the menu. Then type: ```
sudo dpkg --configure -a
``` and press "Enter". It will ask for your password, just type in the one you used to log in. Don't worry if it doesn't show, this is normal security.

You can then exit terminal.

Good luck, and if you have any more questions, feel free to ask.


EDIT: Oh, just saw the bit about not being able to open up a terminal....... Was this because you couldn't find it? If this is the case, try pressing Ctrl+Alt+F2. You might be asked to log in: use the same user name as you would to get into Ubuntu. Then try the above, and type "exit" when you have finished.

---

### Post by gonzalesamy on 2009-04-18
Thanks so much that got everything going but now it is telling me that I have 5 broken filters any idea how to get that fixed.

---

### Post by drs305 on 2009-04-18
> **gonzalesamy said:**
> Thanks so much that got everything going but now it is telling me that I have 5 broken filters any idea how to get that fixed.

If you mean broken packages (*and not 'filters'*:
Open up Synaptic (the ubuntu installer): Main Menu on the top panel, System, Administration, Synaptic Package Manager. If asked for a password, enter your son's password.

In the left pane, near the bottom, click on 'Custom Filters'. Click on 'Broken'in the top left pane and see if there are 5 packages listed in the right pane.

From the top Synaptic menu, Edit, Fix Broken packages.

There is a command line way to do this but the above will get you familiar with the ubuntu gui apps. For the command line way of doing things (simpler):
Open a terminal: Applications, Accessories, Terminal. Or ALT-F2 and tick run in terminal.
```

sudo apt-get update
sudo apt-get install -f

```

If one method doesn't solve it, try the other. If you still have problems, post any error messages you get after running the second command above.

**Added:** For a great read on learning about ubuntu, check out the Ubuntu Pocket Guide link in my signature line.

---

### Post by gonzalesamy on 2009-04-18
Thanks but should I stop the update don't want to mess up the update if I stop it.

---

### Post by drs305 on 2009-04-18
> **gonzalesamy said:**
> Thanks but should I stop the update don't want to mess up the update if I stop it.

If it is paused at the "you must run "dpkg configure..." you can try to correct things before continuing, following lisati's advice first. If it is paused for anything else, it probably isn't going to resume unless you are seeing some disk activity. 

It would be better to try to fix the broken packages before proceeding if you can. The system very well may not let you resume until you have fixed those problems.

---

### Post by gonzalesamy on 2009-04-18
Now getting Errors were encountered while processing:

/var/cache/apt/archives/openoffic.org-core_1%3a2.4.1-2ubuntu2.1_lpia.deb

/var/cache/apt/archives/evolution-common_2.22.3.1-0ubuntu1netbook9_all.deb

E: Sub-process /usr/bin/dpkg returned an error code (1)

Will this ever end.

---

### Post by juancarlospaco on 2009-04-18
sudo rm --verbose /var/cache/apt/archives/openoffic.org-core_1%3a2.4.1-2ubuntu2.1_lpia.deb

sudo rm --verbose /var/cache/apt/archives/evolution-common_2.22.3.1-0ubuntu1netbook9_all.deb

---

