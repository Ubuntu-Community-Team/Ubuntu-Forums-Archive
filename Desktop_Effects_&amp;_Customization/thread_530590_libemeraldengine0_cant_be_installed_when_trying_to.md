---
title: "libemeraldengine0 cant be installed when trying to install emerald"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by czepluch on 2007-08-20
Like the title says i cant install because it says that libemeraldengine0 cant be installed. 

What do i do ?

---

### Post by Happy_Man on 2007-08-20
Are there any other errors? What repo is it coming from? Do you have another version of it installed?

---

### Post by czepluch on 2007-08-21
> **Happy_Man said:**
> Are there any other errors? What repo is it coming from? Do you have another version of it installed?

It is from synaptic and there is no other error.

---

### Post by Happy_Man on 2007-08-21
Hmm... try from the terminal? (Applications --> Accessories --> Terminal) ```
sudo apt-get install libemeraldengine
```

---

### Post by czepluch on 2007-08-21
> **Happy_Man said:**
> Hmm... try from the terminal? (Applications --> Accessories --> Terminal) ```
sudo apt-get install libemeraldengine
```

It says that it cant find the package ? Is it because i havent added the repo maybe ? And what is the repo ?

---

### Post by Happy_Man on 2007-08-21
Hmmm... perhaps installing the metapackage will do the trick. ```
sudo apt-get update
sudo apt-get install beryl emerald-themes
```

---

### Post by MiD-AwE on 2008-01-28
I have the same problem, and I followed your advice. I only get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package beryl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package beryl has no installation candidate

I also get this, when I try to install libemeraldengine0:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libemeraldengine0: Depends: libwnck18 (>= 2.15.90) but it is not installable
                     Depends: emerald (= 0.5.2~git20070925+jbs0) but it is not going to be installed
E: Broken packages

Maybe a bug? How can I get a working file? Thanks.

---

### Post by digitalb0y on 2008-01-28
I'm also having the above issue 
The Error [I]
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libemeraldengine0: Depends: libwnck18 (>= 2.15.90) but it is not installable
                     Depends: emerald (= 0.5.2~git20071006+3v1ubuntu0) but it is not going to be installed
E: Broken packages
[/I]
Ubuntu 7.10 Gutsy Gibbon 
**my /etc/apt/sources.list**
```

deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

```
There currently isn't any version on emerald installed. 

please help:confused: 

Thanks.

-digitalb0y

---

### Post by MiD-AwE on 2008-01-29
Thanks for saying so. At least I'm not the only one. Actually, it looks like others are having the same problem but they either didn't read this post and chose to start new threads or  they don't recognize that their compiz issue is related. Anyway thanks.

---

