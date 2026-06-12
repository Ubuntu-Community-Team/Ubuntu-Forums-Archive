---
title: "open save dialog problems AGAIN"
date: 2017-06-23
forum: Desktop Environments
---

### Post by kellyvotrenom on 2017-06-23
Had a problem with open save dialogs looking different between apps on my new 16.04 install at work - managed to clear that up.

However, after upgrading to  Libre Office (Version: 5.3.3.2) on my 14.04 home machine, the dialogs are different in certain apps. I can no longer see network shares in the shortcuts window. I followed the instructions here -[http://sourcedigit.com/20353-how-to-upgrade-libreoffice-5-in-ubuntu-install-latest-libreoffice-ubuntu/]("http://sourcedigit.com/20353-how-to-upgrade-libreoffice-5-in-ubuntu-install-latest-libreoffice-ubuntu/")

I have attached screenshots of the different dialogs.

What is required to have a uniform open save dialog for all apps?

Thanks

---

### Post by vasa1 on 2017-06-24
How is this thread going to be different than [[SOLVED] open/save dialog different between applications]("https://ubuntuforums.org/showthread.php?t=2358715")?

I thought [Dennis N explained things to you there]("https://ubuntuforums.org/showthread.php?t=2358715&p=13633967#post13633967").

---

### Post by vocx on 2017-06-24
> **kellyvotrenom said:**
> Had a problem with open save dialogs looking **different between apps** on my new 16.04 install at work - managed to clear that up.

However, after upgrading to  Libre Office (Version: 5.3.3.2) on my 14.04 home machine, the dialogs are different in certain apps. I can no longer see network shares in the shortcuts window. I followed the instructions here -[http://sourcedigit.com/20353-how-to-upgrade-libreoffice-5-in-ubuntu-install-latest-libreoffice-ubuntu/](http://sourcedigit.com/20353-how-to-upgrade-libreoffice-5-in-ubuntu-install-latest-libreoffice-ubuntu/)

I have attached screenshots of the different dialogs.

What is required to have a uniform open save dialog for all apps?

Thanks
When you say "apps" are you talking about the different components of LibreOffice, like Writer, Calc, Draw, etc., or do you mean completely different programs, like Gedit, LibreOffice, Nautilus, Rhythmbox, etc.?

I don't think it is exactly possible to make all programs display the same dialog. Why? Because each program, in its internal C, C++ or Python code (or something else), decides what to launch when it shows a dialog such as this.

That is, maybe Nautilus launches a function that says GTK_launch_save(), while another application may use another function, like GTK2_open_save_dialog(). So, these are two different windows, and would show different things. There would be no way for you to force the program to show one window or the other, unless you modify its code.

This is just speculation by the way. I don't know.

Or maybe you can check if this is configurable by launching
```
dconf-editor
```

There seems to be an entry under "org.gtk.settings.FileChooser" to change some parameters.

But I think the issue is the same. Basically, the program itself decides what to show. If many programs internally call the same function, then it seems "standardized", but if each program decided to show their own dialog, then it would be perfectly normal for them, although for the end user this would not be a very good user experience.

---

### Post by kellyvotrenom on 2017-06-27
Yes - Dennis's explanation  described why it was happening in 16.04 - as I understand because of different implementations of GTK. However, those "fixes" don't work with14.04 and I did not have the problem until I made the upgrade to LibreOffice 5.  However, I do regular updates so this may or not be the culprit, I only noticed it soon after the upgrade. Also, part of the upgrade included removing the libreoffice GTK so that made me suspicious.

So to more specific - I went thru pretty much all of the apps on my computer that have an open save dialog and found that is seems to be mostly browser related.  For example, I can no longer see network shares in the open save dialog of several browsers (Firefox, Vivaldi, Opera, Web & Chrome) but in Chromium I can see them.  Thunderbird does not display shares.  Programs like GnuCash and Gnumeric show the shares but Gnumeric has a slightly different look.  Qpdfview, VLC and  Audacity are OK too however Parole is not OK. 

I have seen this referenced in some posts on the Web as a specific bug to Firefox 46 but there is no solution.  Someone suggested to navigate to the .gvfs folder, but for some reason I do not have permission to access that folder (another new problem that I just discovered).  I assume that it is GTK related but have been unable to find resources to point me to a solution.

dconf-editor did produce any useable information.  Again, this is a recent change (past week) on a system that has been running for several years with everything working OK.

Thanks for all your help and suggestions

---

### Post by kellyvotrenom on 2017-06-29
Still looking for a solution as to why my open save dialog - also referred to in other posts as file chooser dialog - changed in a handful of my programs. 

However, to be sure I stated my problem correctly, this is not the same problem as my previous post.  In my new installation of 16.04 I could not see bookmarks in the file chooser dialog.  In my current 14.04 installation everything had been working but then access to network shares disappeared under bookmarks.  Bookmarks have been and still are visisble but bookmarked shares are not listed.

Any help would be appreciated.  I have spent several hours querying Google with as many variations as I can with my problem.  It seems to all point to a GTK / Qt issue but no solutions.

Thanks

---

