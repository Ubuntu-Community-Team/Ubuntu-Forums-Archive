---
title: "Kubuntu-desktop installation problem due to amarok"
date: 2005-09-21
forum: Desktop Environments
---

### Post by agm642 on 2005-09-21
After trying Kubuntu on another computer, I have finally decided to install it on my primary machine. Ubuntu was installed perfectly, but when i type "sudo apt-get install kubuntu-desktop" in a terminal, I get this:

> The following packages have unmet dependencies:
  kubuntu-desktop: Depends: amarok but it is not going to be installed
E: Broken packages

I tried "sudo apt-get install amarok*" in an attempt to find out the problem, and I got this:
> The following packages have unmet dependencies:
  amarok-arts: Depends: amarok (= 2:1.2.4-0ubuntu1~5.04ubp2) but 2:1.2.3-1ubuntu4 is to be installed
  amarok-engines: Depends: amarok (= 2:1.2.4-0ubuntu1~5.04ubp2) but 2:1.2.3-1ubuntu4 is to be installed
  amarok-gstreamer: Depends: amarok (= 2:1.2.4-0ubuntu1~5.04ubp2) but 2:1.2.3-1ubuntu4 is to be installed
  amarok-xine: Depends: amarok (= 2:1.2.4-0ubuntu1~5.04ubp2) but 2:1.2.3-1ubuntu4 is to be installed
E: Broken packages

I guess it means the amarok package on the repos is outdated. Does anybody know what I can do?

---

### Post by mlomker on 2005-09-21
> I guess it means the amarok package on the repos is outdated. Does anybody know what I can do?

Do you have only Ubuntu repos in your sources.list?  If so, then comment the 3rd-party ones out and do an update.

You can also go into synaptic and right-click on amarok...go into Properties and then the Versions tab.  That'll tell you if your sources.list sees more than one copy and where it might be trying to install it from.

---

### Post by agm642 on 2005-09-21
I looked for it in synaptic and I found out that it was trying to install amarok 1.2.3 from the main repos and some newer dependencies from the backports. I commented the backports and I'm OK. Thanks!

---

### Post by zukakog on 2005-09-24
[QUOTE=mlomker]Do you have only Ubuntu repos in your sources.list?  If so, then comment the 3rd-party ones out and do an update.[/QUOTE]

Worked like a charm!  Thanks.

---

