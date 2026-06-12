---
title: "Question about application switcher"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by dentaku65 on 2007-09-06
Hi,
I'm on Gutsy and using CompizConfig I found that there are very poor settings inside CCSM; for example: I would like to set the switching application (Alt-Tab) to all the applications opened on all workspaces and not only on the present workspace, but inside the ccsm under that plugin I have only the general tab as properties... is this something regards the version of CCSM in the Gutsy repos or is the same for everyone?
:confused:

---

### Post by praet on 2007-09-06
There should be a tab in the Application switcher plugin called "Actions", when you define separate key bindings for Next/Prev window as well as Next/Prev window (all workspaces).  So if you wanted Alt+Tab to effect all workspaces, switch the key bindings for "Next window" and "Next window (all workspaces)".

If you do not have the Actions tab then there is a problem with the repo/package you are using.  Make sure you are using the recommended repo (Amaranth): [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

If you were using another repo, you will need to remove all instances of compiz and reinstall.  
See this post:  [http://ubuntuforums.org/showthread.php?t=533476](http://ubuntuforums.org/showthread.php?t=533476)
and this script: [http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)

Alternatively, edit your settings file manually. ~/.config/compiz/compizconfig/Default.ini

---

### Post by dentaku65 on 2007-09-06
Praet really thanks for the answer!
Ok now I'm almost shure that the default ccsm on Gutsy repos is "incomplete", in fact no action tab is available here... maybe I'll open the issue on launchpad.

Den

---

### Post by Inxsible on 2007-09-07
have you installed the compizconfig-settings-manager package ?

---

### Post by dentaku65 on 2007-09-07
> **Inxsible said:**
> have you installed the compizconfig-settings-manager package ?

Yes of course, otherwise I cannot even open the ccsm.
I report the bug on launchpad for Ubuntu Gutsy.

[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/137797](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/137797)

---

