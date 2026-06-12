---
title: "Gnome panels went missing"
date: 2008-05-30
forum: Desktop Environments
---

### Post by reader4 on 2008-05-30
This is very strange, but maybe there is something I am missing.  I was trying to connect to a secure webdav, but there are issues with that right now in Hardy.  So, I installed davfs2 several weeks ago, which didn't help.  Today I uninstalled it.  Everything was fine until I restarted recently (could be totally unrelated to the davfs2 bit, but that was the last system config change).  Now Gnome starts without panels.  When I try to issue 'gnome-panel' from a terminal, I am told gnome-panel is not installed!

Ignoring that oddity, I try to install it and am told "The following packages have unmet dependencies: gnome-panel: Depends: gnome-about (>= 2.10.0-1) but it is not going to be installed".  A check with synaptic confirms it... no gnome-panel, no gnome-about, etc.  Any ideas what happened?

When I try to install gnome-about, I get: " gnome-about: Depends: gnome-desktop-data (= 1:2.22.2-0ubuntu1) but 1:2.22.2-0ubuntu2 is to be installed." 

Is it true that the repositories have incompatible versions of these components?  Am I the only one having this problem?

---

### Post by sisco311 on 2008-05-30
Update the repos:
```
sudo apt-get update
sudo apt-get install gnome-panel
```

---

### Post by reader4 on 2008-05-30
Already done, several times.  I am now looking at my history in Synaptic and notice that when I did the upgrade this morning, gnome-about, gnome-panel and gnome-applets were all removed (along with some others) while gnome-desktop-data was upgraded to 1:2.22.2-0ubuntu2.  My assumption here is that I will just need to be patient until this is ironed out... that the new gnome-panel etc. will be compatible with the new gnome-desktop-data, etc. but hasn't been uploaded yet.  It is quite annoying to have this break in usage - and the associated loss in work-time!

```
Commit Log for Fri May 30 10:03:34 2008


Removed the following packages:
alacarte
fast-user-switch-applet
gnome-about
gnome-applets
gnome-panel
language-support-en
language-support-translations-en
openoffice.org-help-en-gb
openoffice.org-help-en-us
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
ubuntu-desktop

Upgraded the following packages:
gnome-desktop-data (1:2.22.2-0ubuntu1) to 1:2.22.2-0ubuntu2
openoffice.org-core (1:2.4.0-3ubuntu6) to 1:2.4.1~ooh680m14-1ubuntu1
openoffice.org-draw (1:2.4.0-3ubuntu6) to 1:2.4.1~ooh680m14-1ubuntu1
openoffice.org-gnome (1:2.4.0-3ubuntu6) to 1:2.4.1~ooh680m14-1ubuntu1
openoffice.org-gtk (1:2.4.0-3ubuntu6) to 1:2.4.1~ooh680m14-1ubuntu1
openoffice.org-impress (1:2.4.0-3ubuntu6) to 1:2.4.1~ooh680m14-1ubuntu1
openoffice.org-math (1:2.4.0-3ubuntu6) to 1:2.4.1~ooh680m14-1ubuntu1
python-uno (1:2.4.0-3ubuntu6) to 1:2.4.1~ooh680m14-1ubuntu1
```

---

### Post by reader4 on 2008-06-02
Apparently patience was not the answer... the problem still persists.  Is a bug report the next logical step?  I forgot to mention earlier that this a 64-bit Hardy.

---

