---
title: "Why is Ubuntu unity missing some regular text and folder icons on desktop?"
date: 2013-08-20
forum: Desktop Environments
---

### Post by webstuffg on 2013-08-20
1) Why is Ubuntu unity missing some regular text and folder icons on desktop?    Frustrating!  What's frustrating is that it's not missing all regular files and folders, just some.  And to drive user crazy, Ubuntu decides to sometimes allow all icons to show up, and sometimes a few are missing with no rhymne or reason!  ubuntu 12.04 LTS is updated.
However, I then go into home folder -> desktop, I see all the icons there, all the time.   I looked at my work spaces, and it the icons are not hidden there.  Stop releasing buggy software.

2) Where does the unbuntu update files go?   I'd like to go and remove the downloaded compress files (I'm okay with the update) so that it doesn't take up my SSD.  In theory, if ubuntu keep updating and if users don't look for them, wouldn't it keep eating up diskspace?

Thanks.

---

### Post by SweetAurora on 2013-08-20
Is this still 12.04, or did you upgrade to 12.10 or 13.04?

If you are still on 12.04, try first:
```
sudo apt-get install gconf-editor dconf-editor && gsettings set org.gnome.desktop.background show-desktop-icons true
```

if still having problems:
```

gconftool-2 --recursive-unset /apps/compiz-1
unity --reset-icons
unity --reset
sudo reboot
```

---

### Post by Frogs Hair on 2013-08-20
Updates are often only improved replacements for existing files . If a program adds additional features it may result in additional files. An exception would be kernel updates in which the old kernels are not removed and can take up space over time. Old kernels can be removed by the user and some prefer to keep the two latest kernels installed in case of problems with new version.  

> [COLOR=#000000]Stop releasing buggy software.[/COLOR] If you have a specific bug related to desktop  icons file a report at the link. Developers are rare to UF and don't come here to get user feedback, but will respond to bug reports.  

[https://launchpad.net/](https://launchpad.net/)

---

### Post by SweetAurora on 2013-08-20
to remove the dowloaded updates aka "apt-cache" and remove unsed, old packages do:
```
sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
```

Edit: Did my fix help you for your icons?

---

### Post by webstuffg on 2013-08-20
What is UF?  You should have written it out.
I don't get paid to fix someone's obvious bug.  A bunch of needless busy work.  I think there ought to be ratings for each component in ubuntu and allow the good ones float to the top.
There should be some linux laws which bands buggy software.
I went to a conference on git, the the person's presentation was so horrible that I told him that it's nobody's duty to fix his documents but his!  The meeting was a complete waste of time.
Please add the above to the why I dislike Ubuntu thread.  


> **Frogs Hair said:**
> Updates are often only improved replacements for existing files . Ifa program adds additional features it may result in additional files. An exception would be kernel updates in which the old kernels are not removed and can take up space over time. Old kernels can be removed by the user and some prefer to keep the two latest kernels installed in case of problems with new version.  

 If you have a specific bug related to desktop  icons file a report at the link. Developers are rare to UF and don't come here to get user feedback, but will respond to bug reports.  

[https://launchpad.net/](https://launchpad.net/)

---

### Post by GameGuru on 2013-08-20
Sounds like you would rather pay for buggy operating systems and software instead of getting them free.  You must not have been using computer during the Windows 95 era, woah, talk about buggy operating system, features and software.

---

### Post by Frogs Hair on 2013-08-20
Webstuffg I found no problems with your post. UF is Ubuntu Forums a volunteer organization  which has no connection to the with the Ubuntu  development  staff at Canonical. 

 I wanted to inform you that  bugs are addressed at Launchpad and have to be reported to first before there can be a  solution. Many bugs are reported by everyday  users in Alpha  and Beta phases of development and after the final release as well. This is in addition to Canonicals own testing "Buggy" is not very specific and great numbers of users are not affected by bugs even the known reported ones.

---

