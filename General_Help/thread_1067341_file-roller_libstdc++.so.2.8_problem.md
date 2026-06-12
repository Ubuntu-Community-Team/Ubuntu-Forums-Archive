---
title: "file-roller libstdc++.so.2.8 problem"
date: 2009-02-11
forum: General Help
---

### Post by jsnelli2 on 2009-02-11
I just noticed that I am unable to open any .rar files that I have.  When trying to unrar the file in the terminal I get the error

> unrar: error while loading shared libraries: libstdc++.so.2.8: cannot open shared object file: No such file or directory

I have tried reinstalling file-roller with no luck.  I was previously able to rar and unrar files so I do not know what has happened.  I have the libstdc++.so.2.8.tar.gz file, have extracted it but am unable to install it.  Any help is appreciated.

Thanks

---

### Post by mb_webguy on 2009-02-11
Try reinstalling the unrar package, or uninstalling unrar and installing 7zip-rar instead.

Also reinstall the libstdc++5 and libstdc++6 packages.

---

### Post by jsnelli2 on 2009-02-11
Thanks for the reply.  I had already tried reinstalling rar.  I then installed 7zip.  I just tried uninstalling rar and only having 7zip installed.  I'm stilling getting the same error in the terminal.

---

### Post by mb_webguy on 2009-02-11
Did you try reinstalling the libstdc++5 and libstdc++6 packages?

---

### Post by Dougie187 on 2009-02-11
What are you trying to unrar?

Keep in mind the libstdc++ libraries are in the repositories.

---

### Post by jsnelli2 on 2009-02-11
> **mb_webguy said:**
> Did you try reinstalling the libstdc++5 and libstdc++6 packages?

I reinstalled libstdc++6.  I didn't even have libstdc++5 installed, so I installed it.  No luck.

As for what I'm trying to unrar- it makes no difference.  I have tried numerous different rar files.  One that I had even made.  I see they are in the repositories, but am unable to find the one I need in synaptic.

---

### Post by jsnelli2 on 2009-02-11
I think I may have figured out what I have done to cause the problem.  In order to get dvd::rip to work I needed rar 2.71.  I installed that.  Could that be causing the problem with opening rar files in file-roller?  If so, how can I fix this and still have dvd::rip working?

---

### Post by mb_webguy on 2009-02-11
If that *is* the problem, since the ability to unpack rar archives is pretty basic functionality, I'd ditch dvd::rip and switch to something else like Handbrake.

---

### Post by jsnelli2 on 2009-02-11
Alright, I am up for that.  This may be a stupid question...but when running the command sudo apt-get install unrar in the terminal I get the response that the latest version is already installed...yet I know that I installed an earlier version for dvd::rip.  What is my solution?

---

### Post by mb_webguy on 2009-02-11
Try removing it first.  Or you could open Synaptic, check the properties, and if there are multiple versions force the one from the Ubuntu repos.

---

### Post by jsnelli2 on 2009-02-12
I am at a loss here.  Even completely removing rar and unrar from my system leaves me with the same error.  Is there any way I would be able to just install that lib?

---

### Post by jsnelli2 on 2009-02-14
Any ideas?

---

