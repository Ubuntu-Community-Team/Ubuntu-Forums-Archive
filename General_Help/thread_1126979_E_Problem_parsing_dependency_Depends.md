---
title: "E: Problem parsing dependency Depends"
date: 2009-04-15
forum: General Help
---

### Post by sphilli8 on 2009-04-15
G'day

I've been having endless troubles with the repos lately. Seems like everyday I get a new error when I try to upgrade with Adept or Apt-get/Aptitude. Usually I can fix it with some combination of "apt-get -f install" "apt-get clean" "adept-upgrade" etc. Sometimes I have do delete some broken thing and reinstall it after, or go in and fix some error in the archive file. None of that's working for this one. Here's the message:
> E: Problem parsing dependency Depends
E: Error occurred while processing php5 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

When I try to open Adept Updater I get:
> The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem

anyone?

---

### Post by sphilli8 on 2009-04-15
Nevermind, I fixed the main problem. Now there's just a little odd thing going on that I can probably live with, or will fix itself...?

I had to go in and edit:
/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages

In there, I found the php5 package, and it was messed up a little, having the sign "" where there was supposed to be a line break. After that I tried "apt-get update" and got the same error message as before only for a different package. I went back into the file listed above and did a search for every incidence of "", and there were quite a few. I removed them, replacing them with the line break that was supposed to be there.

After that I had to run "apt-get clean" again, and then everything appeared to be working...except that when I try to "apt-get upgrade" I get this message:
> sphilli8@sphilli-top:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  libxine1-misc-plugins python-qt4
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


I don't know why it isn't installing them. The little Adept Update manager exlamation sign thingo (telling me there are some package updates available) is in the corner of the screen, but I click on it, it just says "Update complete" without changing anything, and then the little alert sign stays in the corner.

But yea, that's not too big an issue.

---

### Post by sphilli8 on 2009-04-15
Umm, just in case anyone is interested, the missing sign in the quotation marks in the post above is a little square. I can't find a key on the keyboard for it, I was cutting and pasting before. In the text editor program it's a little square, but in html it comes up as as little box with the numbers 0 0 0 8 in it.

Dunno if that's significant. Both google and ubuntuforums appear averse to that little character.

---

