---
title: "Matlab Folder Access Issue"
date: 2009-03-24
forum: Education &amp; Science
---

### Post by Warthaug on 2009-03-24
I am running matlab on a dual vista/ubuntu 8.10, AMD64.  Matlab is isntalled in both OS's, but due to space limitations both the windows and linux versions are installed on the vista partition (is separate directories - vista under c:\program files, linux under c:\linux programs.

Matlab runs fine in both environments.

The issue I am having is that the linux install of matlab cannot access files/folders on the vista partition - even though it is installed and running from the vista partition!  When I try to switch to a vista directory (wither by clicking through the directory tree, or typing "cd /media/Vista/....." into the command window) I get the following error:

  ???Error using = = > cd
  Cannot CD to XYZ (Name is nonexistent or not a directory)

Where XYZ is the path to the folder I am trying to access.  I have
tried this by both entering the actual path (/media/vista/....) or by
making a link to the folder and accessing it through that.

Anyone know what the problem is, and how I can work around it while
keeping my vista partition, and the matlab .m files on the NTSF partition.

Thanx

Bryan

---

