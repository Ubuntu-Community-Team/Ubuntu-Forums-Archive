---
title: "How to uninstall software that was installed from source"
date: 2006-09-10
forum: Desktop Environments
---

### Post by johnusa on 2006-09-10
Linux newbie using Ubuntu 6.06.  I installed apache 2.2.3 because I wanted I wanted the lastest version (which was not in the repository).   The installation went well.  I then downloaded the latest version of Php (5.1.6).  When I tried to get it to work with apache 2.2.3, I ran into all sorts of problems.   Many of them I was able to resolve but not all of them.  I was advised to just use the packages in the repositories instead of going for the latest version.

Since I didn't use the synaptic package manager or add/remove via the gnome GUI interface for the install, how do I remove apache 2.2.3 and php 5.1.6 from my computer?

Until I know more about linux, I have decided to stick to the software in the repositories and get rid of the software I installed via configure, make and make install.

Thank you in advance for your help!

---

### Post by Ramses de Norre on 2006-09-10
If you're lucky there will be an uninstall script in the tarball, mostly called 'uninstall'. If not you should look in the READ_ME and INSTALL files but you'll be probably forced to manually delete all installed files.

---

### Post by someguyouknow on 2006-09-10
I usually just use adept/synaptic to remove it. not sure if thats the best way but no problems so far.

---

### Post by Ramses de Norre on 2006-09-10
You can't use adept/synaptics for software installed from source.. Only if you used checkinstall.

---

### Post by someguyouknow on 2006-09-10
my fault, that was a .deb

---

### Post by kkinder on 2006-09-10
Sometimes when I install source-software, at the time I do install, I redirect the output of "make install" to a file I refer to on uninstall.

---

### Post by johnusa on 2006-09-10
I will remember that for future use.  Unfortunately, that is not an option for me now!

---

### Post by mcpish on 2006-09-11
Whenever you install software from source, I **Highly Recommend** using "**checkinstall**" instead of "make install" during the final step of compilation.  (ie ./configure && make && checkinstall)

Checkinstall will take the newly compiled program, create a debian package file (deb file) for it, and install it via APT so that the programme will appear in synaptic just like any other package.  The checkinstall program is not installed by default on ubuntu.  Install checkinstall from synaptic or type "sudo apt-get install checkinstall" from the terminal.

What you could do in your situation is simply recompile the same version of the program you compiled, but install it via checkinstall this time.  Since it's still the same version of the software you already have installed, the new deb file will merely re-install over all the existing files that were installed on your first compile but this time there will be a record of these files in a package (deb file) that is accessible from Synaptic.  Then after it's installed, you can simply un-install the programme in Synaptic and choose the option to "completely remove" it.  This should remove all traces of the programme on your system and all of the associated files.  You can then install the other version of the same programme via synaptic (2 entries will be listed, both your compiled version of the programme and the older version in the ubuntu repositories).

---

### Post by johnusa on 2006-09-11
from the root prompt (#), I issued the command but received an error.  Here is the text:
```
# apt-get install checkinstall
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package checkinstall
```
What should I do now?

---

### Post by andiii on 2006-09-11
you need to enable some repositories I guess

Forum -> search -> repositories (or sources.txt)

---

