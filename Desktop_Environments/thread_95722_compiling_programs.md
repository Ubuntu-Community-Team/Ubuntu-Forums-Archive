---
title: "compiling programs"
date: 2005-11-27
forum: Desktop Environments
---

### Post by alma on 2005-11-27
Hi,

I just installed ubuntu and try to compile new programs. In the installation guide is stated that I should use the "make" command. But this command is not in the bin directory and I cannot execute the command.

Who can help me here?

---

### Post by Perfect Storm on 2005-11-27
When you un-comprized the package file (properly it's a tar file of some sort). You need to cd where you unpacked it:

```

cd /where/you/unpacked/it
./configure
make
sudo make install

```

---

### Post by GrumpyBob on 2005-11-27
I think you'll need to install build-essentials as well.

See for example [http://ubuntuforums.org/showthread.php?t=94476&highlight=build-essentials](http://ubuntuforums.org/showthread.php?t=94476&highlight=build-essentials)

Robert

---

### Post by Xian on 2005-11-27
[QUOTE=alma]I just installed ubuntu and try to compile new programs.[/QUOTE]

Please first search [Ubuntu Packages](http://higgs.djpig.de/ubuntu/www/) to make sure what you need isn't already available.

---

