---
title: "Can't install KDE"
date: 2006-07-26
forum: Desktop Environments
---

### Post by nathandh on 2006-07-26
Note I'm very new to Ubuntu :)

So I'd like to install KDE on my Dapper so I do:
```
sudo apt-get install kubuntu-desktop
```

And this is the output I get:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: amarok but it is not going to be installed
                   Depends: ivman but it is not going to be installed
                   Depends: k3b but it is not going to be installed
                   Depends: kaffeine-gstreamer but it is not going to be installed
                   Depends: kaudiocreator but it is not going to be installed
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kdemultimedia-kfile-plugins but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kwin but it is not going to be installed
                   Depends: openoffice.org2-kde but it is not going to be installed
E: Broken packages

```

And I got no idea how to solve this so some help would be greatly appriciated =)

---

### Post by wieman01 on 2006-07-26
Well, you don't want to install KUbuntu (which is the KDE Ubuntu distribution) but KDE. The package name is just not correct.

Use Synaptic and install the right packages (e.g. kde-base, etc.). That should do...

---

### Post by aysiu on 2006-07-26
When you run into dependency errors like that, it's usually because you have conflicting repositories.

Get [a fresh sources.list](http://www.psychocats.net/ubuntu/sources)--remember to paste it **over** your current list and not *add* to the current list.

Then try again.

Use *aptitude*, as *apt-get* will not allow you to remove it easily later: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` For more details, go here: [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

What metapackage you install has nothing to do with dependency errors. If you have the right sources.list, they should all work.

Here's a breakdown of the metapackages from smallest to largest:

**kdebase**: absolute bare essentials
**kde-core**: KDE with a few peripherals
**kubuntu-desktop**: Ubuntu's default packages for KDE
**kde**: the generic default packages for KDE

---

