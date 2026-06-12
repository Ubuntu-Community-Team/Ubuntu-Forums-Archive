---
title: "Value $PATH used by kdesktop and kmenu"
date: 2007-02-26
forum: Desktop Environments
---

### Post by coronya on 2007-02-26
Hello,

I have recently begun to use KDE a bit more, but I have a problem with the $PATH value. I want KDE to verify ~/bin before the other paths when launching an application. That way, if I put firefox in ~/bin, I know the firefox I unpacked in my home dir will be used instead of the one on the system. Under Gnome, this has never been a problem and it worked flawlessly. When I used KDE, I noticed that no matter what I do, it will insist in starting the firefox of the system even if the shortcut is firefox without a full pathname. Even stranger is that if I create a shortcut for a custom program in ~/bin like excelw (a script) that do not exist on the system, it will start as expected. So the PATH is set correctly, but for some reason, KDE ignore ~/bin if the same program exist in /usr/bin. If I start the same program under konsole, everything work as expected.

I checked my .bash_profile and .profile and they are ok (they specify the PATH=~/bin:$PATH, so why is KDE acting like that? Can someone help me on that one?

Thanks,
Richard

Ubuntu 6.10 Edgy
KDE 3.5.6

---

