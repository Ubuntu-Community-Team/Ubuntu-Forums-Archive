---
title: "problem adding KDE packages to 7.1"
date: 2008-04-03
forum: Desktop Environments
---

### Post by Mr noodle on 2008-04-03
In trying to add the basic KDE desktop packages to Gutsy (installed from LiveCD) I found synaptic didn't contain kde-core. I found the KDE core file and dowloaded it independently, and upon installation get an error message: can't install, dependency: arts. 

Is it possible to download the arts file separately or no? I have done some searching, but can't seem to find it.

specs are Compaq laptop M700, 700 mhz pentium, 9gb,256 ram

---

### Post by warp99 on 2008-04-04
To get the KDE desktop with all of the dependencies you just need to open a terminal and type:

```
sudo apt-get install kubuntu-desktop
```

and this will install all of the associated packages to run a KDE desktop. If you cannot get all of the dependencies met then something is wrong with your sources.list file.

---

### Post by tangibleorange on 2008-04-04
I think the problem is that kde-core is in the universe repo. Enable all repos:

System --> Administration --> Software Sources and make sure "main" "universe" "restricted" and "multiverse" are ticked. Save it, close it and go to a terminal:

```
sudo apt-get install kde-core
```

and see if it still errors.

---

### Post by warp99 on 2008-04-04
> **tangibleorange said:**
> I think the problem is that kde-core is in the universe repo.

No, kde-core is a meta package in the main repos:

[http://packages.ubuntu.com/gutsy/all/kde-core/download](http://packages.ubuntu.com/gutsy/all/kde-core/download)

---

### Post by tangibleorange on 2008-04-04
> **warp99 said:**
> No, kde-core is a meta package in the main repos:

[http://packages.ubuntu.com/gutsy/all/kde-core/download](http://packages.ubuntu.com/gutsy/all/kde-core/download)

oops :). oh well, try either of the two commands above ("kubuntu-desktop" if you want the whole Kubuntu package, or "kde-core" for just basic KDE, and tell us the error it gives.

---

### Post by Mr noodle on 2008-04-04
> **tangibleorange said:**
> oops :). oh well, try either of the two commands above ("kubuntu-desktop" if you want the whole Kubuntu package, or "kde-core" for just basic KDE, and tell us the error it gives.

**Sudo apt-get install kde-core**
 
This gives me the error message : "KDE-Core not available but is referred to by another program." Then it goes on to say and I paraphrase, that it could be missing.and also,
"No installation candidate"


**sudo apt-get kde install kubuntu-desktop** 
returns

"invalid operation kde"

I download kde-core but it couldn't install the package becuase of all the dependencies required first.
mainly "arts" . I downloaded arts, but it wouldn't install because arts depended on another file.
And on and on. So doing it this way is way too cumbersome.


The only other way I can think of is to just download Kubuntu.

---

### Post by warp99 on 2008-04-04
> sudo apt-get kde install kubuntu-desktop

That's the incorrect string, try this one:

```
sudo apt-get install kubuntu-desktop
```

Edit:

You don't have to download any packages and install them manually. Everything can be installed with apt-get and have all the dependencies met without any issues, you don't have to reinstall the operating system. The package manager is your friend, let it do all of the work for you.

BTW when you get the Kubuntu-desktop installed your GDM login screen will have an extra session marked KDE from the session drop down list. Choose that to use the KDE desktop.

---

### Post by Mr noodle on 2008-04-04
Ok, I tried the correct string, which I did try before, and it says it can't find the package. I looked in synaptic, its not in there.

---

### Post by tangibleorange on 2008-04-04
Well there must be something wrong with your APT. Are you sure the "main" component is enabled in your synaptic?

---

### Post by warp99 on 2008-04-04
Something is wrong with your sources.list. Please do the following:

```
cat /etc/apt/sources.list
```

and post the results to this thread.

---

