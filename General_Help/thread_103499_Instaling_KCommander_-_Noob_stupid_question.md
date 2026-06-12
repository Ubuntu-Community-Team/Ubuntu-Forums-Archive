---
title: "Instaling KCommander - Noob stupid question"
date: 2005-12-14
forum: General Help
---

### Post by TudorB on 2005-12-14
I`m trying to install [http://www.kcommander.org](http://www.kcommander.org) and I get the following error from the ./configure script:
> 
checking for Qt... configure: error: Qt (>= Qt 2.2.2) (headers and libraries) not found. Please check your installation!

The last lines in config.log are 
> 
onftest.C:18: error: 'QEvent' has not been declared
conftest.C:18: error: 'Speech' was not declared in this scope
configure: failed program was:
#include "confdefs.h"
#include <qglobal.h>
#include <qapplication.h>
#include <qevent.h>
#include <qstring.h>
#include <qstyle.h>
#include <qiconview.h>
#if ! (QT_VERSION >= 222)
#error 1
#endif

int main() {
    QStringList *t = new QStringList();
    QIconView iv(0);
    iv.setWordWrapIconText(false);
    QString s;
    s.setLatin1("Elvis is alive", 14);
    int magnolia = QEvent::Speech; /* new in 2.2 beta2 */
    return 0;
}


What package must I install in order to get this working? I`ve installed almost everything that had QT in its name in Synaptic (I have Kunbuntu, but I preferr Synaptic over Adept)

Thank you

---

### Post by TudorB on 2005-12-14
Come on, anyone...

---

### Post by Ptero-4 on 2005-12-14
[QUOTE=TudorB]Come on, anyone...[/QUOTE]
Have you installed qt3-dev (or some similar package). It's the development libs of qt and is needed to compile kde apps. Also since it talks about qt 2.2.2 you should look for qt 2 compatibility packages.

---

### Post by artnay on 2005-12-14
Are you sure you want to get that installed? I mean, look at the dates. It's not even Qt3 and it doesn't utilize the true power of KDE framework. if you're looking for a MC style file browser, then go get [Krusader]("http://krusader.sourceforge.net/").

The latest stable version is in repos:

Section: universe/utils
Version: 1.60.0-1ubuntu2

Or if you want, you can always go grab the latest development version, conf, make and sudo checkinstall it.

---

### Post by TudorB on 2005-12-14
I have Krusader and I want a file manager with ftp that can actually save passwords and usernames so I don`t have to type them over and over again. Krusader`s FTP panel didn`t allow this, therefor, KCommander it is...

---

### Post by krojc on 2005-12-24
TudorB
Not true. Krusader stores passwords with KWallet. Everytime I connect to ftp it asks me for a username and password, but under it is a small checkbox "keep password".

using 1.70.0beta

I think there were also other solutions, but for that I propose you check the krusader webpage and forum at [www.krusader.org](www.krusader.org) and maybe even ask a question. Krusader is lightyears ahead other twin panel file managers with so many functions, that even developers use their documentation to remember everything :).

---

### Post by infoseeker on 2005-12-26
Read this on their site:

> Please contact us if you want to get a beta tester. We only coding on SuSE systems, so we don't know if KCommander3 run's on other systems. Write a mail to [email]delta_x@gmx.net[/email] 
 


---

### Post by krojc on 2005-12-28
Kcommandrr last update on their site is 04.05.2002

---

### Post by runlevel0 on 2005-12-28
[quote=TudorB]I`m trying to install [http://www.kcommander.org]("http://www.kcommander.org") and I get the following error from the ./configure script:

The last lines in config.log are 


What package must I install in order to get this working? I`ve installed almost everything that had QT in its name in Synaptic (I have Kunbuntu, but I preferr Synaptic over Adept)

Thank you[/quote] 
Oh, My Dog! 

AS I read the subject I thought you was talking about Kommander, the visual programming environment.

Your logs says quite clearly that what you need to compile this stuff is QT-2.2.2. This is a quite old library. You can force things downliadong and installing this lib manually. It's a lotta work, anyway.
Check this link:
[KCommander Download]("http://www.kcommander.org/?area=3") and get the QT3 packages, either the source tarball or the binary packages.

Please note that this software ceased it's developement in 2002 and that it was using a QT version which was quite old even then (QT 2.x dates to the late 1990s) and that the QT3 versions are still beta.

Thus try the binary package. It's an RPM file, but you can change it to a Deb using *alien* (just issue * alien packagename*).

If you fancy doing things the hard way, you can always download QT 2.2.2 and compile it yourself. It's a very lenghty compilation though.

If what you want is a light-weight file manager in the style of widnows Commander, you could try gentoo (the filemanager, not the distro). It's an actual software and you can install it from your default apt- repos w/o any trouble.

You can also split a konqueror window in two and have the same effect.

---

### Post by ajaustin on 2006-01-02
Dear Runlevel0

Have you actually installed gentoo filemanager?

It's a favourite of mine but I can't get it to work with Breezy.  The Copy function gives an error:
```
Couldn't copy "/home/tony/xxx": No such file or directory (code 2)
```

I have always used gentoo fm with other distros and it worked fine so I am very puzzled that it doesn't like Ubuntu.

Tony

---

