---
title: "different reps"
date: 2009-03-24
forum: General Help
---

### Post by jitazoe33 on 2009-03-24
Hey im really new at this whole thing of x's, k's, reps, etc. basically im new at linux. so here is my question: Im currently using Xubuntu but ive heard that with different distros, come a whole diferent repositories list. is there a way maybe to merge open suse's with the add/remove ones for example, or fedora's with ubuntu's and so on? would they work if that's the case? or can someone explain to me if im talking nonsense and they're just the same ones? whats the difference among them? Thanx in advance and sorry about my question... i swear its not a joke!

---

### Post by mb_webguy on 2009-03-25
Different distributions maintain their own repositories, and it's generally a bad idea to mix and match.

Think of distributions like this.  You buy a Dell and your friend buys a Gateway.  They both come with Windows, but if you boot up your computers and take a close look, you'll notice that there are differences.  Each manufacturer makes small changes to the system such as add some manufacturer-specific software.  These could be considered different distributions of Windows.

Linux is the core operating system.  You don't directly interact with it.  The closest you get is using a shell, such as when you open a terminal or use a text-only login.  Everything else is an application, and the specific combination of applications and how they are configured and maintained is what makes the distribution.

Major distributions maintain software repositories in order to help users install software, but also to help maintain system stability.  All of the packages in a distribution's repositories are configured and tested for stability *on that distribution*.  In other words, the specific versions of the software in a particular repository are designed to be compatible with the other software in that repository.

This is especially true of Ubuntu, since it has a stepped release schedule instead of a rolling release schedule.  This means that every six months a new version of Ubuntu is released, with its own repositories.  All of the software in these repositories is tested against the fixed set of software packages for that version of Ubuntu.  Distributions with a rolling release schedule continually update packages in their repositories, so that the distribution is gradually and continuously upgraded.  These distributions naturally contain more up-to-date software, but also tend to be slightly less stable since the set of packages that software packages are tested against is constantly changing. 

Furthermore, the repositories of the major distributions are generally going to contain the same software, just configured for the specific distribution.  So adding repositories of other distributions won't really be of any benefit to you, and will just make your system unstable.

The Ubuntu distribution places emphasis on stability (hence the stepped release schedule), but it also recognizes that some people will want the latest and greatest versions of software.  That's why Canonical (the company behind the Ubuntu distribution) created Launchpad.  Launchpad is a collection of officially-recognized unofficial repositories, called PPAs (Personal Package Archives) maintained by individuals and software development projects.  If you want to make sure you have the most recent version of OpenOffice, for example, you could add the [OpenOffice PPA]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") to your Software Sources.  Because a PPA is essentially a mini-repository, you install software from it just as you would from the Ubuntu repositories and that software is automatically updated by the Update Manager.

Also some software development projects maintain their own independent repositories.  One of the more popular examples is the [WineHQ]("http://www.winehq.org/download/deb") repository.

So if you want to install software that isn't available in the official Ubuntu repositories, or want more recent versions of software than is in the official repositories, your best bet is to look on Launchpad or the developer's website to see if there is a PPA or independently maintained Ubuntu repository for the software.  Your next best option is to look for deb files, which are similar to exe or msi installers in Windows.  As a last resort, you can compile the software from source code.  But adding a repository from a different distribution isn't a good idea at all.

---

### Post by 3rdalbum on 2009-03-25
> **jitazoe33 said:**
> is there a way maybe to merge open suse's with the add/remove ones for example, or fedora's with ubuntu's and so on?

There's absolutely no way to do it; no package manager would be able to cope with the chaos of dependencies even if the package formats were the same.

Ubuntu's repositories are bigger than any other distribution's repositories, possibly including even Debian. What could you possibly want from Fedora or Open Suse's repos?

---

### Post by zvacet on 2009-03-25
In general it is bed idea to have mixed repositories even if all of them are Debian based.I don´t think that any RPM repos will work in Ubuntu.In short,don´t do it.

---

