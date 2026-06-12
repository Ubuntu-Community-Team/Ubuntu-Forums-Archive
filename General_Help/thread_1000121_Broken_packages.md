---
title: "Broken packages"
date: 2008-12-02
forum: General Help
---

### Post by meho_r on 2008-12-02
I've never engaged more broken packages than in Ibex. gv, gnupg2, ocrad, slib... to name just few. Every of those packages broke after fresh reinstall so I don't think it's because of something wrong on system (though it may be). The problem is that those cannot be removed, apt-get install -f doesn't do anything, apt-get remove too. I posted a question in other thread and nobody responded. Here I'd just like to know if anyone else encountered same problem or it's just me.

---

### Post by fragos on 2008-12-02
How about Synaptic Package Manager-> Edit menu-> Fix Broken Packages?

---

### Post by meho_r on 2008-12-02
Thanks for the reply. I tried that too, no success though :(

---

### Post by fragos on 2008-12-02
On another linux platform I had trouble with packages that couldn't be removed or fixed. Each case there was a corrupted symlink that made a shell script decide not to proceed. Removing the offending symlink allowed me to purge/remove and then install. I identified these symlink issues from command line error messages.

---

### Post by grimey44 on 2008-12-04
i have a similar problem. when i try to instal flash in 8.10 it says i have broken packages. im not sure how to fix

---

### Post by meho_r on 2008-12-04
This is not complete solution, but at least you can get rid of that annoying message when try to install anything on your system.

1. If a package just broke, note its name and what wasn't alright during installation (is it postinstall script error or maybe postremove) and run this:
```
ls -al /var/lib/dpkg/info |grep name_of_package
```
This way you'll get info of the package name (it may have .postinstall, .postrm or something like that in its name).

2. Edit that file with a text editor (as root, of course) and at the very beginning you'll notice an entry "set -e". After that entry add:
```
exit 0
```

3. Install/reinstall/remove package again.

---

### Post by grimey44 on 2008-12-04
i try entering that first line in terminal but nothing happens. this is what i get

```

ubuntu@ubuntu:~$ ls -al /var/lib/dpkg/info |grep name_of_package
ubuntu@ubuntu:~$ ls -al /var/lib/dpkg/info |grep name_of_package
ubuntu@ubuntu:~$ 

```

this is me entering it twice after waiting a while.
not sure what to do next

---

### Post by fragos on 2008-12-04
substitute your package name for "name_of_package"

---

### Post by meho_r on 2008-12-05
Here's an example:

On my system, the package "slib" broke (it's a dependency for gnucash).

1. First thing is to take note of message when package broke (that is the one from the terminal if you install through it, or the one from Synaptic if you install through it). In my case, I got a message from Synaptic in a window saying that there was a problem with postinstall script.

2. Since the name of package is "slib" and error is in "postinstall script", I enter this command:
```
ls -al /var/lib/dpkg/info/ |grep slib
```
As a result I got dozen of files which contain "slib" in their names. But I'm interested in one particular file: "slib.postinst" (because the error was in postinstall script; if the error was in preinstall or postremove script, I would have been interested in "slib.preinst" or "slib.postrm" respectively).

3. When I've found the file, I entered this command:
```
sudo gedit /var/lib/dpkg/info/slib.postinst
```
This opened the file in gedit text editor after which I entered, just after "set -e" (about 3rd line in the file):
```
exit 0
```
After that, I saved the file and closed the editor.

4. I reinstalled the package again through Synaptic.

You may try these steps with the particular package you have problems with, just change the name as fragos suggested.

I hope this will help.

---

