---
title: "where to find dependencies for bonfire?"
date: 2006-06-16
forum: Desktop Environments
---

### Post by kinematic on 2006-06-16
I've heard some good things about the bonfire burning app and thought i'd try it out so i don't have all the extra stuff installed that comes with k3b.
I d'loaded the source tar.gz and the bonfire.spec file says i need these dependencies:
BuildRequires:	gettext
BuildRequires:	intltool			>= 0.22
BuildRequires:	desktop-file-utils
BuildRequires:	libgnomeui-devel	>= 2.14
BuildRequires:	gstreamer-devel	>= 0.10.6
BuildRequires:	gstreamer-plugins-base-devel
BuildRequires:	totem-devel		>= 1.4.0
BuildRequires:	libnotify-devel		>= 0.3.0
BuildRequires:	libbeagle-devel		>= 0.2.5
BuildRequires:	nautilus-cd-burner-devel	>= 2.14.0
I looked for these in synaptic but cand find them...i've enabled the following repo's:
deb hxxp://nl.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb hxxp://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src hxxp://nl.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src hxxp://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb hxxp://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src hxxp://security.ubuntu.com/ubuntu dapper-security main restricted
Can anyone tell me  what repo's i need to enable in order to satisfy the dependencies for bonfire?

---

### Post by tronica on 2006-06-16
add this to your sources.list and then sudo apt-get install bonfire

> deb [http://ketsugi.com/ubuntu](http://ketsugi.com/ubuntu) dapper main

---

### Post by kinematic on 2006-06-16
that did it...thnx dude/dudette :D

---

### Post by Pygi on 2006-06-21
[QUOTE=kinematic]I've heard some good things about the bonfire burning app and thought i'd try it out so i don't have all the extra stuff installed that comes with k3b.
I d'loaded the source tar.gz and the bonfire.spec file says i need these dependencies:
BuildRequires:	gettext
BuildRequires:	intltool			>= 0.22
BuildRequires:	desktop-file-utils
BuildRequires:	libgnomeui-devel	>= 2.14
BuildRequires:	gstreamer-devel	>= 0.10.6
BuildRequires:	gstreamer-plugins-base-devel
BuildRequires:	totem-devel		>= 1.4.0
BuildRequires:	libnotify-devel		>= 0.3.0
BuildRequires:	libbeagle-devel		>= 0.2.5
BuildRequires:	nautilus-cd-burner-devel	>= 2.14.0
I looked for these in synaptic but cand find them...i've enabled the following repo's:
deb hxxp://nl.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb hxxp://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src hxxp://nl.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src hxxp://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb hxxp://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src hxxp://security.ubuntu.com/ubuntu dapper-security main restricted
Can anyone tell me  what repo's i need to enable in order to satisfy the dependencies for bonfire?[/QUOTE]

Hello,
You just need to have Main and Universe repositories, which you have already :)
We are going to get bonfire package in official repos soon anyway.

Kind regards,
Mario

---

