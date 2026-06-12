---
title: "Eclipse installing Web Tools Platform WTP 0.7.1"
date: 2005-10-23
forum: Desktop Environments
---

### Post by mindhaq on 2005-10-23
Hello,

I'm using Eclipse 3.1.1 for Java Development under Ubuntu, which I installed via Synaptic. Now I'd like to use the WTP V0.7.1. I tried to install via the update manager, as described in [this tutorial](http://www.eclipse.org/webtools/development/updatesite/updatesite.html). After I click on "Select required", all dependend libraries are selected for install, too. But there is one thing missing, as there is the following error message:

"Web Standard Tools Feature (0.7.1) requires plug-in "org.eclipse.tomcat"."

Same happens with 0.7.0.

Well, this plugin is not in the plugins-directory. I'm not sure if it is missing from the ubuntu packages, or if there is something else wrong, maybe a missing package like in [my other problem I had with the Eclipse Update Manager]("http://ubuntuforums.org/showthread.php?t=79194").

Has anybody an idea for a solution, apart from installing WTP by hand?

---

### Post by MarcDM on 2005-10-25
same problem over here dude. And google is not helping much.

---

### Post by mindhaq on 2005-10-26
I worked around this problem by removing all Eclipse related packages, and downloading a tarball vom eclipse.org. This is not as comfortable as apt, especially regarding future updates or plugins.

But - all you have to do is untar and create a starter in your Gnome menu. Updates are available via Eclipses internal updater, which will then also work flawlessly.

In my opinion it is a very good move to include Eclipse into the package repositories, but there are still some limitations, obviously because of the modularization done by the package maintainer(s). Hopefully this is fixed in future updates of the package. Maybe I find the time to put this into bugzilla, what do you say?

---

