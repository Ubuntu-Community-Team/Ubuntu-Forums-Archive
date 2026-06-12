---
title: "Adobe Acrobat installs but doesn't run"
date: 2006-05-04
forum: Desktop Environments
---

### Post by WrathofthePenguin on 2006-05-04
I downloaded and installed Adobe Acrobat directly from Adobe (I didn't use Automatix). Installation went smoothly, but it doesn't appear to want to run.

When I try to open a pdf file directly, the Adobe Acrobat banner comes up, clears after about a second, then nothing.

I ran it from the command line and got the exact same behavior with no error messages.

Anybody have any ideas?

---

### Post by hw-tph on 2006-05-04
When you don't have any error messages to help pinpointing the problem, it is usually wise to try to get them. In this case, type **acroread** in a terminal to see what it might output before it bails out.


Håkan

---

### Post by louis_nichols on 2006-05-04
I don't know whay this would happen. What I want to say is tht [acroread]("http://packages.ubuntu.com/breezy/text/acroread") is in the repos for breezy, easily instalable through synaptic, no need for automatix.

So, my suggestion would be to spare yourself the pain, uninstall the adobe package and install the deb.

---

### Post by WrathofthePenguin on 2006-05-05
[QUOTE=hw-tph]When you don't have any error messages to help pinpointing the problem, it is usually wise to try to get them. In this case, type **acroread** in a terminal to see what it might output before it bails out.


Håkan[/QUOTE]

I agree with you completely - but I wasn't sufficiently clear in my post. That's what I did when I said I tried it at a command line - I should have said I did it in a terminal window. Thanks for the reply, though.

---

### Post by WrathofthePenguin on 2006-05-05
[QUOTE=louis_nichols]I don't know whay this would happen. What I want to say is tht [acroread]("http://packages.ubuntu.com/breezy/text/acroread") is in the repos for breezy, easily instalable through synaptic, no need for automatix.

So, my suggestion would be to spare yourself the pain, uninstall the adobe package and install the deb.[/QUOTE]

Great news - using Synaptic installed it and it works now. This makes me very happy because I can now view pdfs that Evince and others were having trouble with. Thanks!

---

### Post by louis_nichols on 2006-05-05
[QUOTE=WrathofthePenguin]Great news - using Synaptic installed it and it works now. This makes me very happy because I can now view pdfs that Evince and others were having trouble with. Thanks![/QUOTE]
:) glad it works ok

---

### Post by isidfe on 2006-05-09
It seems that Acrobat (as downloaded from Adobe) needs the libstdc++5 package installed. This is not installed by default on Ubuntu 5.10, but you can install it through any of the package managers.

---

