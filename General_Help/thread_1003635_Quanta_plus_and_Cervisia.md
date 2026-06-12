---
title: "Quanta plus and Cervisia"
date: 2008-12-06
forum: General Help
---

### Post by MikeEagling on 2008-12-06
Hi,

I have installed the *kdewebdev* package from the Intrepid repositories so that I can use Quanta Plus.

Upon initial installation Quanta complained about Cervisia being missing, despite it being installed as part of the package. Thinking that it would be a good thing to learn I've configured CVS and the Cervisia client to the point where I have a repo that I can check files in and out of. I thought the initial lack of configuration might be the problem. However, Quanta still complains that Cervisia is missing.

From the Quanta Plus [plugin config documentation](http://docs.kde.org/kde3/en/kdewebdev/quanta/configure-plugins.html) this looks like a problem with the "libtool file", *kde3/libcervisiapart.la*, but I don't understand what or where this might be. I've tried finding the appropriate file for the KFileReplace plugin, which is apparently ok but this doesn't seem to exist on my system so I'm at a loss as to what needs to be done.

Any ideas?

Thanks in anticipation,
Mike

---

### Post by fsando on 2008-12-14
Did you find a solution yet?

I'm interested too

---

### Post by Lyconyx on 2008-12-15
I've got a similar problem here's the error message:

```
Some applications required for full functionality are missing:

- KImageMapEditor [http://www.nongnu.org/kimagemap/] - editing HTML image maps will not be available;
- Cervisia [http://www.kde.org/apps/cervisia] - CVS management plugin will not be available.

You may download the applications from the specified locations.
```

Like you I have everything installed so not sure whats up, I tried reinstalling.

Note that I'm on Ubuntu not Kubuntu (since Quanta is a KDE app)

Lyconyx

---

### Post by uzi09 on 2009-01-03
> **Lyconyx said:**
> I've got a similar problem here's the error message:

```
Some applications required for full functionality are missing:

- KImageMapEditor [http://www.nongnu.org/kimagemap/] - editing HTML image maps will not be available;
- Cervisia [http://www.kde.org/apps/cervisia] - CVS management plugin will not be available.

You may download the applications from the specified locations.
```

Like you I have everything installed so not sure whats up, I tried reinstalling.

Note that I'm on Ubuntu not Kubuntu (since Quanta is a KDE app)

Lyconyx

same here....

i wonder though. did you guys install kimagemapeditor-kde4 and cervisia-kde4 packages?

i have the above to kde4 packages and quanta (regular) package since it could not install the kde4 one for some reason.

should that cause problems? any way to tell quanta where to look for the programs?

---

### Post by ahusain on 2009-02-01
so as far as i can tell installing kimagemapeditor-kde4 is something of a downgrade. when i installed it i got the message 

```

The following packages will be REMOVED:
  kdewebdev kimagemapeditor
```

and after that when i started quanta again i got an extra error message that i didn't have before

---

### Post by jasmines on 2009-03-10
Use /usr/lib/kde4/cervisiapart.so
It solved, for me!

---

### Post by jasonditz on 2009-08-30
Go to Settings>Configure Plugins...

select the CVS Management (Cervisia) and Configure

Change the file name to wherever your version of Cervisia is installed (as the above user notes, default would be kde4/cervisiapart.so

---

### Post by randomenthusiast on 2009-11-01
I also have the same problem.  I am using Ubuntu 9.04 and trying to get Quanta to be fullly functional. I tried configuring the Cervisia plugin to point to kde4/cervisiapart.so , but it comes up with yet another error
```
-the file kde4/cervisiapart.so is not installed or it is not reachable.
```Also - that file does exist and is as reachable (file permission-wise) as any of the other plugin files.

Cervisia runs fine if you run it separately, so I wonder if this even matters.  I think it just means that you don't have it integrated into Quanta's interface.

---

### Post by muncrief on 2009-11-15
Edit: This solution doesn't work!!! See my following post for one that does!!!

I had the same problems installing Qaunta Plus under Karmic. It compalined that Cervisia, KImageMapEditor, and kxsldbg were not installed. It appears that Quanta Plus is a KDE3 application, while the programs its complaining about are KDE4. Note that it didn't complain about Konsole not being present, but when I looked at the plugin settings it said konsole was also invalid.

I solved the problem by first installing cervisia, konsole, kimagemapeditor, and kxsldbg, and then modifying the plugin locations by going to Settings->Configure Plugins and changing the following entries:

CVS Management (Cervisia) to kde4/cervisiapart.so
KImageMapEditor to kde4/libkimagemapeditor.so
Konsole to kde4/libkonsolepart.so
XSLT Debugger to kde4/libkxsldbgpart.so

Just a warning, I have never used Quanta Plus before so I wasn't able to test whether this mix of KDE3/KDE4 apps actually work, however Quanta Plus didn't complain about them once I made the above changes.

If by chance they don't work Karmic includes kimagemapeditor-kde3 and kxsldbg-kde3 which work with the default locations, but it doesn't include kde3 versions of cervisia and konsole.

---

### Post by muncrief on 2009-11-16
OK, forget my previous post. The solution I proposed didn't work. However, I found another solution that works perfectly (at least with what I've done so far).

Basically I downloaded three packages from Ubuntu Hardy which contained KDE3 versions of what was missing, installed them, and now I have a fully functional Quanta Plus system on Karmic x86_64. Note that I didn't have to "force" install anything, so it appears the downloaded packages have all dependencies met and are fully compatible with Karmic.

First download the appropriate libcvsservice0, konsole, and cervisia packages for your architecture from the following URLs:

[http://packages.ubuntu.com/en/hardy-backports/libs/libcvsservice0](http://packages.ubuntu.com/en/hardy-backports/libs/libcvsservice0)
[http://packages.ubuntu.com/hardy/konsole](http://packages.ubuntu.com/hardy/konsole)
[http://packages.ubuntu.com/hardy/cervisia](http://packages.ubuntu.com/hardy/cervisia)

Now install a few dependencies:

sudo aptitude install cvs kdelibs4c2a

Now change to the directory that you downloaded the packages to and execute the following commands to install them (of course changing the names if the versions are different):

sudo dpkg -i libcvsservice0_3.5.10-0ubuntu1~hardy1_amd64.deb
sudo dpkg -i cervisia_3.5.9-0ubuntu1_amd64.deb
sudo dpkg -i konsole_3.5.9-0ubuntu7_amd64.deb

Now install Quanta Plus and the KDE3 versions of kimagemapeditor and kxsldbg:

sudo aptitude install quanta kimagemapeditor-kde3 kxsldbg-kde3


That's it. You should be up and running now.

---

### Post by tidmarsh on 2010-02-24
I've had the same problem, and after ignoring it for a few months, finally got around to fixing it.

What worked for me (in Jaunty) was open the Configure Plugins window (Settings > Configure Plugins) and then click Configure for each one witha red check (Cerevisia, KImageMapEditor, Konsole). I cleared the file name box for each one and then filled in the location box by browsing to and selecting the directory for each application, all of which were contained in usr/share/kde4/apps.

---

### Post by gwoodruff on 2010-10-07
I changed the locations as described in the previous post and now get green checks for all plugins. When I try to launch any the kde4 plugins from the plugins menu in Quanta I get the following error:
The CVS Management (Cervisia) plugin could not be loaded.
Possible reasons are:
- CVS Management (Cervisia) is not installed;
- the file /usr/lib/kde4/cervisiapart.so is not installed or it is not reachable.
I have read in other posts that Quanta does not recognize the kde4 versions of these programs. Can those who have kde4 versions launch them from the plugins menu?

Gary

---

### Post by nutznboltz on 2010-10-24
> **muncrief said:**
> OK, forget my previous post. The solution I proposed didn't work. However, I found another solution that works perfectly (at least with what I've done so far).

Basically I downloaded three packages from Ubuntu Hardy which contained KDE3 versions of what was missing, installed them, and now I have a fully functional Quanta Plus system on Karmic x86_64. Note that I didn't have to "force" install anything, so it appears the downloaded packages have all dependencies met and are fully compatible with Karmic.

First download the appropriate libcvsservice0, konsole, and cervisia packages for your architecture from the following URLs:

[http://packages.ubuntu.com/en/hardy-backports/libs/libcvsservice0](http://packages.ubuntu.com/en/hardy-backports/libs/libcvsservice0)
[http://packages.ubuntu.com/hardy/konsole](http://packages.ubuntu.com/hardy/konsole)
[http://packages.ubuntu.com/hardy/cervisia](http://packages.ubuntu.com/hardy/cervisia)

Now install a few dependencies:

sudo aptitude install cvs kdelibs4c2a

Now change to the directory that you downloaded the packages to and execute the following commands to install them (of course changing the names if the versions are different):

sudo dpkg -i libcvsservice0_3.5.10-0ubuntu1~hardy1_amd64.deb
sudo dpkg -i cervisia_3.5.9-0ubuntu1_amd64.deb
sudo dpkg -i konsole_3.5.9-0ubuntu7_amd64.deb

Now install Quanta Plus and the KDE3 versions of kimagemapeditor and kxsldbg:

sudo aptitude install quanta kimagemapeditor-kde3 kxsldbg-kde3


That's it. You should be up and running now.

You need to put package holds on some of them:

$ sudo dpkg --set-selections
libcvsservice0 hold
konsole hold
cervisia hold
^D
$

Updated: it also helps to pin the packages.  I did it on my system by creating this file:

$ cat /etc/apt/preferences.d/kde-web-dev.pref

Package: konsole
Pin: version 4:3.5.9-0ubuntu7
Pin-Priority: 1001

Package: cervisia
Pin: version 4:3.5.9-0ubuntu1
Pin-Priority: 1001
$

With the package "holds" in effect but prior to adding that preferences file, update-manager showed the package names "konsole" and "cervisia" greyed-out.  With that preferences file the package names are not displayed.

---

### Post by evarie on 2011-07-04
I get in trouble in these steps:


Now change to the directory that you downloaded the packages to and execute the following commands to install them (of course changing the names if the versions are different):

sudo dpkg -i libcvsservice0_3.5.10-0ubuntu1~hardy1_amd64.deb
sudo dpkg -i cervisia_3.5.9-0ubuntu1_amd64.deb
sudo dpkg -i konsole_3.5.9-0ubuntu7_amd64.deb


Can you update the solution for the year 2011?

---

### Post by rmil on 2011-09-25
For Ubuntu and other users that have already installed cervisia:

First should locate where is the location of cervisiapart.so with command in terminal

**locate cervisiapart.so**

for me it is /usr/lib/kde4/cervisiapart.so

then go to plugins settings under settings menu in quanta and change directory location accordingly.

Worked for me

---

