---
title: "Clarification of CLI syntax..."
date: 2009-04-22
forum: General Help
---

### Post by David C. on 2009-04-22
I just installed Glade using $sudo apt-get install glade. It installed the app, but what I'm confused about is this:
```

The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libsigc++-2.0-dev fakeroot libxml++2.6-dev libgtk1.2
  linux-headers-2.6.27-7 nvidia-settings etl-dev libgtkmm-2.4-dev
  linux-headers-2.6.27-7-generic libdv-bin python2.5-doc libcairomm-1.0-dev
  libglibmm-2.4-dev dkms ffmpeg libxml2-dev libgtk1.2-common libxml++2.6-2
  libopenexr-dev libimlib2 libpangomm-1.4-dev libilmbase-dev libavdevice52
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autoconf automake automake1.4 glade-common m4
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc glade-doc
  libglade2-dev menu
The following NEW packages will be installed:
  autoconf automake automake1.4 glade glade-common m4
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 3130kB of archives.
After this operation, 10.8MB of additional disk space will be used.
```


I've seen this each time I've run the 'apt-get install...'

If I run 'sudo apt-get autoremove' do I need to list all the libraries? Or does it just know what to remove. I don't want to remove something that is needed. I've sinced closed the terminal and am curious to know if I run the autoremove or do a I run sudo apt-get remove..." listing the libraries.

---

### Post by CatKiller on 2009-04-22
Packages that are installed as a dependency to a package that you want to install are marked as "automatically installed." If these are no longer required, because the packages that depend on them are removed, they can be removed all in one go. apt-get autoremove will go through these packages and remove the ones that are no longer needed.

aptitude does this automatically. It's one of the differences between apt-get and aptitude.

---

### Post by David C. on 2009-04-22
Uh, aptitude? Forgive my ignorance here, but is that what "apt" in apt-get means?

---

### Post by James_Lochhead on 2009-04-22
> **David C. said:**
> I just installed Glade using $sudo apt-get install glade. It installed the app, but what I'm confused about is this:
```

The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libsigc++-2.0-dev fakeroot libxml++2.6-dev libgtk1.2
  linux-headers-2.6.27-7 nvidia-settings etl-dev libgtkmm-2.4-dev
  linux-headers-2.6.27-7-generic libdv-bin python2.5-doc libcairomm-1.0-dev
  libglibmm-2.4-dev dkms ffmpeg libxml2-dev libgtk1.2-common libxml++2.6-2
  libopenexr-dev libimlib2 libpangomm-1.4-dev libilmbase-dev libavdevice52
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autoconf automake automake1.4 glade-common m4
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc glade-doc
  libglade2-dev menu
The following NEW packages will be installed:
  autoconf automake automake1.4 glade glade-common m4
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 3130kB of archives.
After this operation, 10.8MB of additional disk space will be used.
```


I've seen this each time I've run the 'apt-get install...'

If I run 'sudo apt-get autoremove' do I need to list all the libraries? Or does it just know what to remove. I don't want to remove something that is needed. I've sinced closed the terminal and am curious to know if I run the autoremove or do a I run sudo apt-get remove..." listing the libraries.

No you do not need to list all the libraries. The command sudo apt-get autoremove simply removes all the packages that you no longer need. It shouldn't break anything.

---

### Post by James_Lochhead on 2009-04-22
> **David C. said:**
> Uh, aptitude? Forgive my ignorance here, but is that what "apt" in apt-get means?

I believe apt here means Advanced Packaging Tool.

---

### Post by David C. on 2009-04-22
Okay...thanks. I ran the autoremove worked fine. It did remove Python 2.5 documents though, no worries, just popped them back in there.

---

