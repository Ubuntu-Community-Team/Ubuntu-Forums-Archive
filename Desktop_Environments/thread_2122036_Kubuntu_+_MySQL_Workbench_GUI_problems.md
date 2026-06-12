---
title: "Kubuntu + MySQL Workbench GUI problems"
date: 2013-03-03
forum: Desktop Environments
---

### Post by _0R10N on 2013-03-03
Hi, I recently installed MySQL-Workbench on my fresh Kubuntu install only to realize that there's some serious issues. Created schemas are not shown (I checked via command line that they exist), just an empty list, not even the default schema is visible. This problem also affects other sections of the program, for example, when using the data modeler I cannot add columns to the table, since the corresponding tab is rendered completely empty.

I tried re installing the app without any luck. This doesn't happens on Fedora+KDE nor on Ubuntu.

---

### Post by allezlesbleusno1 on 2013-03-04
> **_0R10N said:**
> Hi, I recently installed MySQL-Workbench on my fresh Kubuntu install only to realize that there's some serious issues. Created schemas are not shown (I checked via command line that they exist), just an empty list, not even the default schema is visible. This problem also affects other sections of the program, for example, when using the data modeler I cannot add columns to the table, since the corresponding tab is rendered completely empty.

I tried re installing the app without any luck. This doesn't happens on Fedora+KDE nor on Ubuntu.

Have you been able to find a solution to this issue?

I'm suffering from the same exact problem and have also tried re-installing the app to no avail.  I'm using latest Kubuntu and previously I was using Ubuntu + Cinnamon and never suffered from this issue.

---

### Post by _0R10N on 2013-03-05
No, I haven't been able to solve this out. I know that Mysql-Workbench doesn't support KDE very well. Nonetheless, I have another box with Fedora+KDE and this is not happening, it has its occasionally crashes, but I haven't detected a GUI problem so far.

Anyway, last night I gave up and installed Ubuntu+Gnome.

As a final note, I tried removing the app (which I had installed from Kubuntu repository) , deleting the conf folder placed in ~/.mysql/workbench (or something like that) and downloading the version available on Mysql site. It didn't work.

If you come with a solution to this, would you let me know?

Regards!

---

### Post by allezlesbleusno1 on 2013-03-11
> **_0R10N said:**
> No, I haven't been able to solve this out. I know that Mysql-Workbench doesn't support KDE very well. Nonetheless, I have another box with Fedora+KDE and this is not happening, it has its occasionally crashes, but I haven't detected a GUI problem so far.

Anyway, last night I gave up and installed Ubuntu+Gnome.

As a final note, I tried removing the app (which I had installed from Kubuntu repository) , deleting the conf folder placed in ~/.mysql/workbench (or something like that) and downloading the version available on Mysql site. It didn't work.

If you come with a solution to this, would you let me know?

Regards!

I certainly will let you know if I do come up with a solution.  It's kind of frustrating as I'm running managing my MySQL databases by terminal commandline since I can't use workbench.

---

### Post by allezlesbleusno1 on 2013-03-14
UPDATE: So for several reasons, I ended up reinstalling Kubuntu.  After installing Workbench on my new Kubuntu installation, it looks like resultset data shows up  in the appropriate pane when executing queries.  The only thing that still doesn't show up properly is when I select the database schema in the left pane and when expanding the table tree, it shows up as "fetching" and never returns the table names.  Kind of frustrating that it still doesn't show up entirely but at least it's showing more than before.  

Also, I am not running latest version of Workbench, rather I installed the version from the software center -- I may upgrade it later and see if this fixes that issue.  I'll update this thread once I do that.

---

