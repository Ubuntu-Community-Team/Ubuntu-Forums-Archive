---
title: "VirtualBox to start automatically?"
date: 2009-04-05
forum: General Help
---

### Post by Robotman on 2009-04-05
A friend of mine gave me his laptop to fix.  The problem?  Vista.  The solution?  Ubuntu. :D
He wants his Windows XP to run in VirtualBox, however, so I've done that for him too.  What I'd like to know is can VirtualBox be made to automatically boot Windows XP inside itself when Ubuntu starts?
(An aside that some may find humorous... under Vista I thought the laptop screen was shot and needed to be replaced... Under Ubuntu it's vibrant and sharp. :lolflag: )

---

### Post by 3Miro on 2009-04-05
The console command is:

```

VirtualBox -startvm name_of_the_machine

```

There is a place under System -> (Admin/Prefs) that you can enter your own startup scripts/start up commands. Try it.

---

### Post by Robotman on 2009-04-05
Thanks for the reply!  That works great.  In my case, I had to go to System/Preferences/Sessions and then "Add".  I had to rename the virtual machine in VirtualBox though, it wouldn't load anything with spaces, underscores or not.
Again, thanks!

---

### Post by Nathanael Culver on 2009-04-05
[OK, I see I got her late. Apologies for the duplication.]

> **Robotman said:**
> can VirtualBox be made to automatically boot Windows XP inside itself when Ubuntu starts?

Open a terminal and run the following:

**VBoxManage list vms**

Look for either the name or the UUID of the VM you want to run. Now enter the following (specifying either the VM name or its UUID):

**VBoxManage startvm {uuid OR vmname}**

Finally, to start the VM automatically, go to System/Preferences/Sessions, click Add, and enter a name and the above command line. You should be good to go.

--Nathanael

---

### Post by ju2wheels on 2009-04-05
> **Robotman said:**
> Thanks for the reply!  That works great.  In my case, I had to go to System/Preferences/Sessions and then "Add".  I had to rename the virtual machine in VirtualBox though, it wouldn't load anything with spaces, underscores or not.
Again, thanks!

You have to quote the portion with spaces and it must match the name you used in the Virtualbox GUI exactly.

```

Virtualbox -startvm "VM Name"

```

---

### Post by 3Miro on 2009-04-05
> **Robotman said:**
> Thanks for the reply!  That works great.  In my case, I had to go to System/Preferences/Sessions and then "Add".  I had to rename the virtual machine in VirtualBox though, it wouldn't load anything with spaces, underscores or not.
Again, thanks!

You can use slash before the spaces and it works:
```

VirtualBox -startvm Windows\ XP

```

---

### Post by Robotman on 2009-04-06
Thanks for the helpful tips everyone.  Is it possible to delay a startup app?  If I wanted Ubuntu to wait 20 seconds before it loaded the virtual machine in VB, how would I do that?

---

### Post by 3Miro on 2009-04-06
> **Robotman said:**
> Thanks for the helpful tips everyone.  Is it possible to delay a startup app?  If I wanted Ubuntu to wait 20 seconds before it loaded the virtual machine in VB, how would I do that?

You will have to use a script. I will try to put something together, it will probably be in optimal, but it should work.

---

### Post by 3Miro on 2009-04-06
Copy paste this in a file somewhere (use gedit):

```

#!/usr/bin/python

import time, sys, os

time.sleep(20)

os.popen("VirtualBox -startvm name_of_the_machine")


```

It basically waits 20 seconds and then calls the Virtual Box command. Put the name of your machine in "name_of_the_machine".

Save the file and give it some name, suppose you put it in Documents and call the file "vbstart.py". Then you need to set the permissions (either use nautilus to set the files as executable or use:
```

chmod 700 Documents/vbstart.py

```

The from where you are setting the VB as startup commnad, give the comand:
```

/home/you_name/Documents/vbstart.py

```

Give it a try if you want. I am sure someone will come up with a cleaner solution, but the above should work.

---

