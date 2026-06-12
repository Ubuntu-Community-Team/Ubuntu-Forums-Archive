---
title: "Synaptic questions"
date: 2006-01-10
forum: Desktop Environments
---

### Post by Razorback on 2006-01-10
Is it normal to have to install dependencies after an application is installed?  The reason I ask is I downloaded and installed clamAV but it did not install all the packages it needed to work.  This also happened with a game I installed.

Also, is it normal to get a warning that installed repositories aren't available when reopening Synaptic after they have been updated?

Thanks

---

### Post by Ampersand on 2006-01-10
It's possible that there was a problem with either your connection or the servers when you were installing packages, and not all of them were downloaded; other than that I've not come across any similar problems.

---

### Post by Razorback on 2006-01-10
Would it be best to reinstall or add the packages manually to ensure it is properly installed?  The reason I ask is that clamAV references clamAV-data (I think) and it appears I can download this file.

---

### Post by lamego on 2006-01-10
There must be a problem with the package definition itself.
My experience is tha synaptic will not install a final package unless the dependencies are met (one of the dependencies failing to download/install is one of the cases).
The clamav package definition maybe wrong and is lacking a depedency...

---

### Post by az on 2006-01-10
[QUOTE=Razorback]Would it be best to reinstall or add the packages manually to ensure it is properly installed?  The reason I ask is that clamAV references clamAV-data (I think) and it appears I can download this file.[/QUOTE]
Well, if you install stuff by hand, you have a greater change of messing up your system.  It may also be that one package does not neccessarily need the package to run, but is useless without it.  In that case, it is a reccommends, or a suggested, but not a dependancy.  You can see those and install them using synaptic.

---

### Post by Razorback on 2006-01-10
I am sorry, by manually I meant using synaptic to install the dependencies not using a manual install.  I guess one of the dependencies might have failed to install.  I will try installing the other packages and see what happens.  Thanks for the responses.  I am a noob to Linux but am really impressed with it so far! :)

---

