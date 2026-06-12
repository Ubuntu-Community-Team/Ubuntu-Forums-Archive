---
title: "Where does GNOME stop and Ubuntu begin?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by dudinatrix on 2005-10-18
I read a review on Ubuntu a while ago, and they posed basically the same question.  Being a relative Linux-newbie (I've been using Kubuntu for 6 months), I'm curious what exactly makes Ubuntu Ubuntu.

Can anybody provide some examples on where Gnome stops and Ubuntu begins?

---

### Post by SickTwist on 2005-10-18
There are a few Ubuntu-specific apps like the Ubuntu Device Database front-end, Update Manager and Usplash but the majority of programs are just part of Free Software land. Of course, nothing is stopping other distributions from using the Ubuntu specific apps.

The [GNOME project]("http://www.gnome.org/") releases a set of desktop programs that are integrated with each other. Most of these programs are included with Ubuntu but not all of them (for instance, Ubuntu uses Mozilla Firefox instead of [Epiphany]("http://www.gnome.org/projects/epiphany/")). All GNOME apps use [GTK+]("http://www.gtk.org/") for their toolkit.

The rest of the included programs are just apps that use GTK+ such as [Serpentine]("http://s1x.homelinux.net/projects/serpentine/").

Sometimes the lines are a little blurry because anyone can contribute to a project.

---

### Post by jasongrieves on 2005-10-18
Ubuntu is a distribution.  In my mind a distribution has to accomplish a couple things
1)provide a package manager (i.e. apt-get)
2) provide a desktop environment (i.e. gnome)
3) provide packages to fill in the gaps where desktop ends (.e. open office, firefox, etc)

you can check out the gnome website for all gnome packages that you see.  Everything else is Ubuntu or packages ubuntu has brought in.

For example a simple one is the usplash screen you see when booting.  All ubuntu.

---

### Post by ChrisTheGeek on 2005-10-18
Ubuntu is a Linux distribution.  Gnome is one possible visual interface that works with Linux - KDE being its best known competition.  The distinction between graphical interface and operating system isn't so clear in the Windows world where the interface is the only way to use the operating system.  In Linux however they are different things.  A linux system may have multiple graphical interfaces or none at all.

The skill of creating a distribution is in the packages that are chosen, the integration and consistency between the packages and in the little touches like the artwork (not to mention the community spirit and values, support, security fixes, development procedures...etc).  Ubuntu is a particular combination of all of these.  Gnome is 'just' a graphical front end that makes it easy to access Ubuntu's other chosen packages.  Having said that, both the Gnome and Ubuntu projects share similar goals - such as simplicity and ease of use.  They also have pretty synchronised release schedules every 6 months.  I believe there is also a lot of co-operation between the two projects.

Hope this helps a bit.

---

### Post by David Marrs on 2005-10-18
I think Gnome is more than *just* a graphical front-end, it's an entire platform in its own right, especially from a developer's stand point. If someone asks me what OS I run, I'm increasingly inclined to say Gnome, or Gnome/Linux. 

As for where Gnome ends and Ubuntu begins, it isn't always clear. Ubuntu take the Gnome platform and the Debian distro and tweak them to work the way they want. Where the changes were made isn't always clear, however. For example, I recently got worried that Gnome had removed a feature when in fact Ubuntu had merely hidden it. Stuff like this shows why it pays to actively read the press and join the community.

Most distro quirks tend to be in how they're run, as opposed to what they ship. Debian stable is released when ready (usually over years) while Ubuntu releases are timed to coincide with Gnome releases (every six months). Fedora continues to see active support after it's released but uses a different package management system. The devil's in the details, I'm afraid. The best thing to do is read a distro's web site and FAQ to get an idea of how it works. Broadly speaking, they all basically do the same thing.

---

