---
title: "Adobe plugin"
date: 2006-08-18
forum: Desktop Environments
---

### Post by wpshooter on 2006-08-18
I have finally gotten Abobe Acrobat Reader installed but how do I get rid of the attached message ?

What is it that I am supposed to be looking for on the Adobe site ?

Thanks.

---

### Post by louis_nichols on 2006-08-18
Actually, it tells you that you need to install the package acroread-plugins from the repos. Acroread, which is Adobe Reader is also found there, easily installable.

---

### Post by wpshooter on 2006-08-18
I don't understand.  When I do a search on "Acroread" in synaptic it shows two items both of which are already marked as being installed.

The message indicates that this is something to be found on the Adobe website but my question is exactly what is it that I am looking for on their site.  The message does not make this very clear or at least not to me.

Thanks.

---

### Post by wpshooter on 2006-08-18
This is one of the things I do not like about Linux.

Even though you install a program like Acrobat Reader using the automatix utility, you still wind up not being able to properly use it because there are usually little things like this that don't get installed and the application will still not function properly and then the instructions that are given on any error/warning messages are not sufficient to allow you to know what to do to solve the problem.  I assure you I did not have these problems with M/S !!!

---

### Post by louis_nichols on 2006-08-18
Don't worry! You always have a bunch of other problems with M/S, that you don't with Linux, to which answers can never be found. Before I completely erased Win XP from my machine, it wasn't even booting anymore; after the splash screen, it went all black and stayed that way. Now, I've had such problems in Linux, but the difference is that most of times I knew why and where to find an answer, whereas with M/S that is impossible anyway you look at it.

Plus, the Reader is proprietary software, and the lack of info is totaly Adobe's fault. Ubuntu has no responsability in that.

Now, for the reader, I think you went about it the wrong way. Automatix was a useful app back in the beginning of the Breezy days, but ever since Dapper came out, I never felt any need for it.

What you need to do about Adobe Reader is this:
[LIST=1]
[*]Follow instructions [here ]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html")to enable extra repos
[*]Open synaptic and install packages acroread mozilla-acroread and acroread-plugins
[/LIST]

That worked flawlessly for me. Any other error thrown out by Adobe's reader can not be solved without Adobe giving all of us the necessary info. That would mean for many releasing the source code, but I'd say a simple troubleshooting section would do.

---

