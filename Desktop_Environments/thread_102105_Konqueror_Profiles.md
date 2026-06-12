---
title: "Konqueror Profiles"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Permafrost91 on 2005-12-11
I'm running KDE 3.5 on Dapper and I don't have the konqueror sidebar. I can't even find how to enable it. Any thoughts?

Also, on my Gentoo machine I have two sub-menus in Konqueror when I right-click on a file or folder that I find really helpful: Copy-To and Move-To. How can I get these menus back on Kubuntu?

---

### Post by limit223 on 2005-12-11
[http://www.kubuntu.org/faq.php](http://www.kubuntu.org/faq.php)
How do I change Konqueror back to the default KDE profiles?
"Kubuntu Breezy comes with a simplified Konqueror profile to make things more use friendly compared to default KDE.

To get back to the default KDE profiles:

sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc"


Also to make active this settings in your ~/.kde you have to: 

rm ~/.kde/share/apps/konqueror/konq-kubuntu.rc

and leave just konqueror.rc file in the directory.

You'll find all KDE settings that your have in Gentoo as normal.

---

