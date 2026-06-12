---
title: "QApt Batch Installer requires authentication"
date: 2017-09-24
forum: Desktop Environments
---

### Post by fbusse on 2017-09-24
For some days now, I happen to see popups from a "help program for system notifications" (sorry for bad translation from German "Hilfsprogramm für Systembenachrichtigungen"), complaining about "incomplete language support, additional packages required":
[IMG]http://forum.kubuntu-de.org/index.php?action=dlattach;topic=19191.0;attach=7823;image[/IMG]

Left-clicking this message calls a window requiring authentication to "Install or remove packages":
[IMG]http://forum.kubuntu-de.org/index.php?action=dlattach;topic=19191.0;attach=7817;image[/IMG]
The given PIDs are for 'qaptworker3' and 'qapt-batch' - however, I don't want to give system access, without information about what *exactly* is going on.

Following [a hint in the German Kubuntu forum]("http://forum.kubuntu-de.org/index.php?topic=19191.msg122968#msg122968"), I called ```
sudo apt-get install language-pack-kde-de language-pack-de language-pack-de-base language-pack-gnome-de-base language-pack-gnome-de aspell-de hunspell-de-de hyphen-de ingerman libreoffice-help-de libreoffice-l10n-de manpages-de mythes-de wngerman wogerman wswiss
``` to have "all German language packs installed". [Output]("http://forum.kubuntu-de.org/index.php?topic=19191.msg122972#msg122972") gave no hints to anything missing - however, the damn popup still keep coming up.

Any ideas?

My system:
[IMG]http://forum.kubuntu-de.org/index.php?action=dlattach;topic=19191.0;attach=7819;image[/IMG]

---

