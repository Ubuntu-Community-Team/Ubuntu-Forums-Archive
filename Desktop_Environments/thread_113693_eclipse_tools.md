---
title: "eclipse tools"
date: 2006-01-06
forum: Desktop Environments
---

### Post by melgrim on 2006-01-06
Not sure this is where it should be but still...

I can't find the "eclipse-cdt" package anywhere.

How can I install it?

---

### Post by Mr Frosti on 2006-01-06
I stumbled across this article using Google:

[http://sources.redhat.com/ml/eclipse/2003-q3/msg00068.html]("http://sources.redhat.com/ml/eclipse/2003-q3/msg00068.html")

It outlines how to install Eclipse on Debian (What Ubuntu is built on), so the instructions should be almost identical. The only issue would be with possible dependencies. 

Download the eclipse package for Red Hat (RPM):

[http://people.redhat.com/~jhealy/eclipse/snapshot-20030802-eclipse-2.1.0-12.i386.rpm]("http://people.redhat.com/~jhealy/eclipse/snapshot-20030802-eclipse-2.1.0-12.i386.rpm")

Convert this from a .rpm file to a .deb file (for Ubuntu / Debian) using the following command:

```
sudo alien snapshot-20030802-eclipse-2.1.0-12.i386.rpm
```

Now, install this package using whatever alien creates as the file name:

```
sudo dpkg -i snapshot-20030802-eclipse-2.1.0-12.i386.deb
```

Either it will succeed or fail. If it fails because of missing dependencies, open up Synaptic package manager by clicking on "System" -> "Administration" -> "Synaptic". Remove the package marked to be installed by doing a search for "eclipse"

---

### Post by cstudent on 2006-01-06
[QUOTE=melgrim]Not sure this is where it should be but still...

I can't find the "eclipse-cdt" package anywhere.

How can I install it?[/QUOTE]


Add this url to Eclipse's update manager.

[http://download.eclipse.org/tools/cdt/releases/eclipse3.1](http://download.eclipse.org/tools/cdt/releases/eclipse3.1)

Look under Help>Software Updates>Find and Install>Search for new features to install. Be aware that you may have to run Eclipse as root during this update process depending on how you have Eclipse installed. If root has ownership of the Eclipse directory the update will give errors if you try to run it as normal user.

---

### Post by melgrim on 2006-01-07
looks like the problem is solved.

I've added the url and it's now working fine.

thanks for the help.

---

