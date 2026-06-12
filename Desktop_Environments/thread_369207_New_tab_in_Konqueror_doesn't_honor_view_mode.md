---
title: "New tab in Konqueror doesn't honor view mode"
date: 2007-02-24
forum: Desktop Environments
---

### Post by astronic on 2007-02-24
Dear Forums,

the following does not work as expected in Kubuntu edgy:

1) Open Konqueror (via System Menu->Home Folder), set view mode to "Detailed List View" and save this setting to the view profile "Kubuntu file manager".

2) Close Konqueror and open it again. The home folder now appears in view mode "Detailed List View".

3) Open a new tab and enter some directory (for example by clicking on the "Home" button in Konqueror or by entering a path manually). The view mode used now is NOT "Detailed List View" as it should be, but "Icon View".

Can somebody tell me how I can make Konqueror open new tabs in "Detailed List View"? I don't think it is a KDE bug, because using KDE 3.5.5 on Gentoo everything works fine.

Thanks in advance!

Regards,
Stefan

---

### Post by h@l0 on 2007-03-22
I'm a complete noob to linux and have the same problem.  Can't find the answer anywhere.  So far it seems like I'd have to go through every folder and set to Detailed View Mode instead of Icon View.  Too much trouble. There must be a way to set Detailed View as default for all windows in Konqueror.

Have seen it suggested that you add

[MainView Settings]
SaveViewPropertiesLocally=0
ToggableViewsShown=konq_sidebartng
ViewMode=konq_detailedlistview

to
 /home/[username]/.kde/share/config/konquerorrc
 /root/.kde/share/config/konquerorrc   and
usr/share/kubuntu-default-settings/kde-profile/default/share/config/konquerorrc

and restarting with "kfmclient openProfile [profilename]"
but it doesn't work.

Can anyone help with this?

---

### Post by bertilow on 2007-04-04
> **h@l0 said:**
> I'm a complete noob to linux and have the same problem.  Can't find the answer anywhere.  So far it seems like I'd have to go through every folder and set to Detailed View Mode instead of Icon View.  Too much trouble. There must be a way to set Detailed View as default for all windows in Konqueror.

The following page mentions an easy workaround for all lovers of "Detailed list view":

[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/69168](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/69168)

---

