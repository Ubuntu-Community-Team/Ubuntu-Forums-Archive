---
title: "KOffice problems"
date: 2006-06-06
forum: Desktop Environments
---

### Post by DarkOx on 2006-06-06
I recently did a clean install of Dapper onto my laptop, and so far everything's been working great - except that I can't get KOffice to run. I installed it via Adept, and Adept tells me it's installed, but no KOffice icons have been added to my menu.
When I try starting Kword or Kspread with the terminal I get the following errors:

> koffice (lib kofficecore): ERROR: kspreadpart.desktop not found.
koffice (lib kofficecore): ERROR: Run 'kde-config --path services' to see which directories were searched, assuming kde startup had the same environment as your current shell.
koffice (lib kofficecore): ERROR: Check your installation (did you install KOffice in a different prefix than KDE, without adding the prefix to /etc/kderc ?)

I expect it's that last error about the prefix that's causing the problem, but I haven't been able to find what prefix I need to add to get this to work. Has anyone else had this problem? Any help would be appreciated.

---

### Post by tonyr on 2006-06-06
I installed **koffice** with **adept** just now without any problem.  I'm running
Dapper, updated yesterday (3jun06, USA/PDT).  Here is my **/etc/kderc**:
```

[Directories]
userProfileMapFile=/etc/kde-user-profile

[Directories-default]
prefixes=/usr/share/kubuntu-default-settings/kde-profile/default/

```

but my gut feel is that the install went south somehow.

---

### Post by dkuhlman on 2006-06-15
[QUOTE=DarkOx]I recently did a clean install of Dapper onto my laptop, and so far everything's been working great - except that I can't get KOffice to run. I installed it via Adept, and Adept tells me it's installed, but no KOffice icons have been added to my menu.
When I try starting Kword or Kspread with the terminal I get the following errors:

```
koffice (lib kofficecore): ERROR: kspreadpart.desktop not found.
koffice (lib kofficecore): ERROR: Run 'kde-config --path services' to see which directories were searched, assuming kde startup had the same environment as your current shell.
koffice (lib kofficecore): ERROR: Check your installation (did you install KOffice in a different prefix than KDE, without adding the prefix to /etc/kderc ?)
```

I expect it's that last error about the prefix that's causing the problem, but I haven't been able to find what prefix I need to add to get this to work. Has anyone else had this problem? Any help would be appreciated.[/QUOTE]

I have this same problem.  I installed koffice using aptitude.  Was/Is there a solution?  I've done a Web search and also searched the Ubuntu install forum, but could not find anything.

I tried running the following:

```
dpkg-reconfigure koffice
```

but it did not help.

Still, the error message suggests that there is some configuration process that needs to be run or re-run while specifying something like my ~/.kde directory.

Can anyone tell me where I can go to read about doing this setup?

Dave

---

### Post by vigleik on 2006-06-15
I had the same problem a few days ago. Then I did a clean install and now it's working. I'm afraid I have no idea why it didn't work the first time but did work the second time, but at least this seems to be a common problem.

Vigleik

---

### Post by dkuhlman on 2006-06-15
[QUOTE=vigleik]I had the same problem a few days ago. Then I did a clean install and now it's working. I'm afraid I have no idea why it didn't work the first time but did work the second time, but at least this seems to be a common problem.

Vigleik[/QUOTE]

Vigleik -

Thanks for help.

But, what did you cleanly install.  Kubuntu?  Koffice?

I've tried reinstalling Koffice, and that does not seem to help.  I also tried uninstalling Koffice and then doing the install again.  The installation finishes with no error messages.  But, when I run kword, I get those same errors.

I don't think I'm ready to try to reinstall all of Kubuntu.  I guess I'll keep searching.

Dave

---

### Post by vigleik on 2006-06-16
[QUOTE=dkuhlman]But, what did you cleanly install.  Kubuntu?  Koffice?
[/QUOTE]

Yeah, I installed kubuntu again. Or actually ubuntu, and then I install kde and koffice. Just reinstalling koffice didn't work for me either. It's a drastic step though, so if I had spent more time customizing my install I wouldn't have done it. As it were, a couple of other things weren't working for me either so I thought maybe I hosed up my install somehow. Hence the fresh install of 6.06.

Vigleik

---

### Post by dkuhlman on 2006-06-16
More follow-up -- This morning after turning on and booting my machine, kword, kspread, etc now work fine.  In addition, KDE Office apps are present in my KDE menu under KDE -> Office.

My guess is that perhaps installing KOffice requires that I logout and then logon to a new KDE session in order to complete the process.  But, since I've already installed KOffice, I can't test that.  If and when I need to install KOffice on another machine, I'll try to remember to try logging  out and back on to KDE.

If installing KOffice requires logging out and back on to KDE or something else, I wish that were documented somewhere.

> Yeah, I installed kubuntu again. Or actually ubuntu, and then I install kde and koffice. Just reinstalling koffice didn't work for me either. It's a drastic step though, so if I had spent more time customizing my install I wouldn't have done it. As it were, a couple of other things weren't working for me either so I thought maybe I hosed up my install somehow. Hence the fresh install of 6.06.

Yes, reinstalling the operating system seems drastic to me.  If installing KOffice requires that, I call it a "usability issue".

At any rate, thanks for the suggestions and encouragement.

Dave

---

