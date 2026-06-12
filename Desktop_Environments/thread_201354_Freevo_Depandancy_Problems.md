---
title: "Freevo Depandancy Problems"
date: 2006-06-21
forum: Desktop Environments
---

### Post by computergee on 2006-06-21
Hi, I'm new here, but not to ubuntu. I am trying to install freevo, and got all the repositories set up. But when I type "sudo apt-get install freevo", I get the following.

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freevo: Depends: python (< 2.4) but 2.4.2-0ubuntu3 is to be installed
E: Broken packages

From what I can tell I have the right version of python, but since this version was installed with ubuntu the version is named differently, so the installer won't see it as the correct version. How do I get the installer to recognize the version of python to be the correct version?

---

### Post by lamego on 2006-06-21
You must have some non ubuntu repositories. I have all the ubuntu repos and the application is not available. Being a 3rd party repository would explain the dependency problems .

```
lamego@lamego-desktop:~$ sudo apt-get install freevo
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package freevo
lamego@lamego-desktop:~$
```

---

### Post by computergee on 2006-06-21
Yes, I added the freevo repository.

deb [http://freevo.sourceforge.net/debian/](http://freevo.sourceforge.net/debian/) unstable main

I also added:
deb [http://download.gna.org/praksys](http://download.gna.org/praksys) praksys/
deb [http://download.gna.org/praksys](http://download.gna.org/praksys) praksys-testing/

Because the freevo repo dosnt have all of its dependancies for some reason. I have all the dependancies, but the thing is it is not seeing python as the right version because its version is named "2.4.2-0ubuntu3" instead of "2.4". Is there a way to get past this?

---

### Post by lamego on 2006-06-21
Well, it doesn't matter if you do have the software itself, dependencies are baed on package names, nor on their contents. That freevo debian pckage that you are trying to install was not build on/for Ubuntu Dapper.
I don't believe there is an ignore dependencies option (at least I didn't found it on the apt-get manual).

---

### Post by computergee on 2006-06-21
Oh, thanks. Is there a way to rename that package? Or maybe install a dumby package with the right name? If not how do you suggest I install freevo? Compile it's source?

---

### Post by lamego on 2006-06-21
In my oppinion compiling from the source is the best option for you case.

---

### Post by Ptero-4 on 2006-06-21
The reason it's not seeing the right version of python isn't b/c of the ubuntu naming. It's b/c it requires python 2.3 or earlier.

---

