---
title: "Photoshop problem with wine"
date: 2006-01-16
forum: Desktop Environments
---

### Post by kennyhow on 2006-01-16
I had Kubuntu installed and ran Photoshop fine with wine.  Now that I have switched over to Ubuntu and don't want anything to do with KDE...I haven't been able to run Photoshop.  I have Photoshop 7.  I'm using Wine version 0.9.5.

Photoshop installs fine.  But, when I try to run it, it looks like it's loading everything ok.  After it gets past the loading screen it appears to start to load the toolbars but it doesn't...it stops and gives me the following error message.  Still in the wine format...so it's not wine crashing, it's photoshop.

```
Unable to continue because of a hardware or system error.
Sorry, but this error is unrecoverable.
```

Anyone possibly know why this is happening on gnome and didn't on kde?  I thought it might have been my video drivers or some change I made to my xorg file.  But, I changed everything back and it's still not working.  I've uninstalled wine...deleted every file related to wine after uninstalling it (removing with apt-get).  I am lost.  Please help me find my way.

---

### Post by kennyhow on 2006-01-17
Anyone?

---

### Post by eddiewalker on 2006-01-17
[http://bugs.winehq.org/show_bug.cgi?id=4081#c6](http://bugs.winehq.org/show_bug.cgi?id=4081#c6)

I have the same problem.  Looks like it should be fixed in the next package, so either give it a few weeks or downgrade to the version in the ubuntu rep. because it works.

---

### Post by Zillion on 2006-01-26
Hmm it also doesnt work with Wine 0.9.6. Same error. Neither could get the CS version to run, it gives error > Could not complete your request because certain required files were not found in the Adobe Photoshop CS Required folder. Please reinstall Photoshop to restore these files.

Any help to get it working would be appreciated, I am pretty much a n00b on linux. tx

---

### Post by quinnman on 2006-01-26
As far as I know the only version of Photoshop thats works is 7, but only with wine up to version 0.9.2 It is strange, but newer versions of Wine are no longer able to run Photoshop. It may change in the future, but if you need Photoshop now -> downgrade to 0.9.2

---

### Post by Zillion on 2006-01-26
Where can I get 0.9.2 and how can I install it? tx

---

### Post by Kimm on 2006-01-26
you dont happen to have done something to your .wine directory?

> 
Could not complete your request because certain required files were not found in the Adobe Photoshop CS Required folder. Please reinstall Photoshop to restore these files.


Sounds like a registry key might be missing.

---

### Post by Zillion on 2006-01-26
Nope, its a known problem according to [http://appdb.winehq.org/appview.php?versionId=1815](http://appdb.winehq.org/appview.php?versionId=1815)

But Photoshop 7 and CS (see comments on link) are reported to run on Wine 0.9.2.

Ok, now how do I get and install 0.9.2 thank you :)
Can I use one of these files? [http://prdownloads.sourceforge.net/wine](http://prdownloads.sourceforge.net/wine)

---

### Post by Zillion on 2006-01-27
Well I gave up with Wine.. though I managed to install Dreamweaver 8 trial succesfully with it.

Photoshop 7 I now have running with Crossover Office 5. It seems to work fine so far :)

---

### Post by andrija1989 on 2006-01-30
hey 
i just started using ubuntu... and i was wondering what program can i use instead of photoshop and where can i find this program?

---

### Post by RAOF on 2006-01-30
You can use the gimp - you'll find it already installed under "Applications -> Graphics -> GIMP".  It's pretty powerful.  Comparable to Photoshop, I belive (although I've never needed to do any really serious image manipulation).

---

### Post by Sutekh on 2006-01-30
You can use the 'GIMP' a Photoshop alternative.  IMHO its far above Photoshop and free!  It should have already been installed with Ubuntu.  Check Applications -> Graphics -> GIMP Image Editor.

---

### Post by Perfect Storm on 2006-01-30
You can also use Pixel 32 but it's not free. [http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12)

---

### Post by quinnman on 2006-02-01
[QUOTE=Zillion]Where can I get 0.9.2 and how can I install it? tx[/QUOTE]
I guess you installed Wine with Synaptic. Than you have a following source in repo list "deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/" otherwise you can add it.
I hope that Synaptic allows you to install older version. Is's somewhere in the menu (I am not at home currently, I don't know exactly).

---

### Post by SolidAndShade on 2006-02-02
The newest version of Wine (0.9.6, I think) doesn't work with Photoshop and I got the exact same error you did when using it. I downloaded that version of Wine after using Automatix to add the Sourceforge wine repository to my list of repositories in Synaptic. So I removed that repository, removed Wine and then installed the older Ubuntu-specific version of Wine, the one with "ubuntu" in the version number. After that, Photoshop worked just fine.

---

### Post by quinnman on 2006-02-03
Too bad :-( There's no way to install the older version. Only the latest. But the SolidAndShades idea should work. Ubuntu official repositories host some pre-beta version.

---

