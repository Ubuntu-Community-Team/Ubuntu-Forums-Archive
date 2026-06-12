---
title: "Eclipse building workspace too slow"
date: 2009-05-04
forum: General Help
---

### Post by burakvarhan on 2009-05-04
Dear all,

I downloaded and installed Eclipse Ganymede and the corresponding CDT plugin for C/C++ programming on Ubuntu 9.04 with sun-java jdk. I had the same configuration before on Ubuntu 8.10.

I have this C++ project with more than 50 classes. When I build my project  by CTRL+B it shows the "Building Workspace" dialog and takes more than 4 minutes to finish building.

Does anyone have an idea or solution for why it takes that much long to build a project? considering that it was OK with Ubuntu 8.10.

I suspect that it re-builds all files despite I modify a single class. If this is the case is there a way to build only the modified class in Eclipse CDT.

Thanks

---

### Post by lvleph on 2009-05-04
I have had the same issue with the latest build, but on 8.10. In windows it was much faster; I really hate that.

---

### Post by jamesdcarroll on 2009-05-04
I get that when I have too many projects open in the workspace, at least in Java.  You can right click on a project and close it.  What I'll do sometimes is Ctrl-A/Close to close all of them, then right click Open Related projects. In Java there's the 'Build Automatically' feature that you may want to turn off if there one in the CDT.

---

### Post by burakvarhan on 2009-05-04
I just realized that it is the linking stage that takes too long not compiling! 
Now, if someone could tell us how to boost g++ linker the problem would get solved...

Does the order of libraries affect linking? I am using "z, bz2, mysqlclient, pthread" libraries in this order.

---

