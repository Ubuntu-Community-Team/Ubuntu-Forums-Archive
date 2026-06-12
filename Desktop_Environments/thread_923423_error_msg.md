---
title: "error msg"
date: 2008-09-18
forum: Desktop Environments
---

### Post by lanr01 on 2008-09-18
I am getting this error msg when I try to install any updates, or anything really..

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

 What do I need to do?

Thank you
Rick

---

### Post by mcduck on 2008-09-18
First thing would be to try what it tells you to do.. Open a terminal and run "sudo dpkg --configure -a".. ;)

---

### Post by anotherdisciple on 2008-09-19
> **mcduck said:**
> First thing would be to try what it tells you to do.. Open a terminal and run "sudo dpkg --configure -a".. ;)

I see you are new to the forums... so just in case you don't know how to get to the terminal and input that command....

Go to:
(Applications > Accessories > Terminal)

---

### Post by loudnlownoma on 2008-09-19
Not to hijack, since it may be relavent if the OP tries this and fails, what happens when that command doesn't work in the terminal?  My connection died during an install of some stuff from Synaptic and I received the same error.  Thinking the same way, ran the command in the terminal and it starts well enough but then seemingly hangs in the process.  Enough Ctrl-C and I get back to a prompt, but trying again does the same.  

From the dpkg --help command, I tried ```
sudo dpkg -r -a
``` to remove the pending installations, which did allow me to access Synaptic/Update Manager again.  However, while installing updates it tried to install the erroneous packages again and now I receive the message all over again...

Can get more specific if needed, or start my own thread if the powers that be prefer, but am at work currently so specific info may have to wait.  Thanks in advance!

---

### Post by Bucky Ball on 2008-09-19
Have you gone to Synaptic package manager and checked to see if the culprit is ticked? If it is, untick and when you apply those changes it will probably uninstall the half installed package.

---

### Post by loudnlownoma on 2008-09-19
> **Bucky Ball said:**
> Have you gone to Synaptic package manager and checked to see if the culprit is ticked? If it is, untick and when you apply those changes it will probably uninstall the half installed package.

When I ran into the problem, Synaptic would give the above error message telling me to run that command.  I can't recall if it would allow me to do anything in Synaptic at that point or not, and will check when I get home.  Although shouldn't the remove pending tag I tried earlier that got it working momentarily remove the pending installation for good?

---

### Post by Bucky Ball on 2008-09-19
> **loudnlownoma said:**
> Although shouldn't the remove pending tag I tried earlier that got it working momentarily remove the pending installation for good?

Yep, that is the idea. Then close Synaptics, open, find the package again, tick and reinstall. This time you should get the full install without getting cut halfway through. :)

---

