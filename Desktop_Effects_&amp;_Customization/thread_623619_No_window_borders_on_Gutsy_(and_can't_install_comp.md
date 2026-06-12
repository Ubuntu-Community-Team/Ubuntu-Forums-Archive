---
title: "No window borders on Gutsy (and can't install compiz-gnome)"
date: 2007-11-26
forum: Desktop Effects &amp; Customization
---

### Post by k31k0 on 2007-11-26
Hi.

I have few problems after last week's automatic upgrade. I was using Compiz effects normally until I installed some upgrades last week (I remember that upgrades were something about Compiz, but I don't remember what packages were upgraded).
First problem is that I have no window borders when I enable Compiz. After reading few posts on this forum about this problem, I tried to install package "compiz-gnome" so I could enter command "gtk-window-decorator --replace" into Command field of WIndow Decoration plugin.
When I tried to install that package, I get an error saying:
```
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
  compiz-gnome: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages
```

I don't know how to fix this and I'd really like to have Compiz effects on my laptop.

Regards, Sasha.

---

### Post by Znort_Ubern00b on 2007-11-26
What graphics card are you using???

---

### Post by k31k0 on 2007-11-26
I have HP nx7400 laptop with Intel GMA 950 that uses computer's RAM. I know that this graphics card isn't much, but it run Compiz effects without a problem.

---

### Post by Forlong on 2007-11-26
Are you using any third-party repositories and/or have the gutsy backoports enabled?

---

### Post by k31k0 on 2007-11-26
I am using Automatix2 with it's repositories (at least this repositories are listed between *#AUTOMATIX REPOS START* and *#AUTOMATIX REPOS END*):
```
deb http://archive.canonical.com/ubuntu gutsy partner
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
```

So, when I have those repositories enabled, I get the following error:
```
sudo apt-get install compiz-gnome
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
  compiz-gnome: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages
```

However, when I comment those repositories, I get even more errors:
```
sudo apt-get install compiz-gnome
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
  compiz-gnome: Depends: compiz-core (= 1:0.6.0+git20071008-0ubuntu1.1) but 1:0.6.2+git20071119-0ubuntu1~gutsy1 is to be installed
                Depends: compiz-plugins (= 1:0.6.0+git20071008-0ubuntu1.1) but 1:0.6.2+git20071119-0ubuntu1~gutsy1 is to be installed
E: Broken packages
```

So I don't know what to do. And I can't tell from your question should I use gutsy backports or not? :confused:

---

### Post by Forlong on 2007-11-26
No, do not enable backports and partner.

Disable any non-official repositories and update your sources:
```
sudo apt-get update
```
Then try this:
```
sudo apt-get -f install
```

---

### Post by k31k0 on 2007-11-27
Nothing... :(
Here is the message of *sudo apt-get -f install*:
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

And if I try to install compiz-gnome, I get the same error as before:
```
sudo apt-get install compiz-gnome
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
  compiz-gnome: Depends: compiz-core (= 1:0.6.0+git20071008-0ubuntu1.1) but 1:0.6.2+git20071119-0ubuntu1~gutsy1 is to be installed
                Depends: compiz-plugins (= 1:0.6.0+git20071008-0ubuntu1.1) but 1:0.6.2+git20071119-0ubuntu1~gutsy1 is to be installed
E: Broken packages
```

---

### Post by Forlong on 2007-11-27
> **k31k0 said:**
> ```
The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-core (= 1:0.6.0+git20071008-0ubuntu1.1) but 1:0.6.2+git20071119-0ubuntu1~gutsy1 is to be installed
                Depends: compiz-plugins (= 1:0.6.0+git20071008-0ubuntu1.1) but 1:0.6.2+git20071119-0ubuntu1~gutsy1 is to be installed
E: Broken packages
```
Did you really disable the backports? Because those are backported packages.

What's the output of ```
dpkg -l | grep compiz
```

---

### Post by k31k0 on 2007-11-27
Yes, I commented out the backport sources. But anyway, I've reinstalled Ubuntu because I was playing with settings for wireless on my laptop and something got messed up so I decided to make a fresh install.
Thanks for the help anyway ;)

---

