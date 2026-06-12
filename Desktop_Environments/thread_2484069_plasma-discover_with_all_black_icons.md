---
title: "plasma-discover with all black icons"
date: 2023-02-16
forum: Desktop Environments
---

### Post by alexis0b on 2023-02-16
Hi guys!

Version 22.04
Kernel 5.15

I've been playing around with Ubuntu (Lubuntu, precisely) since some weeks now and I was trying to install GOverlay and make it work, without any success (I want to check in-game temperatures and performance in general cause the system is running slower than what it could, in my opinion, and I suspect that the problem are my optimization skills and lack of familiarity with Linux). In the process I needed to install some kind of libraries and during this, I lost the plasma-discover application (the Linux "app-store"), which was a default program. I managed to reinstall it from the terminal but now all the icons contained in it are just black, and the problem seems to be spread all over the plasma environment. 

I attach images for clarity

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291798&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291799&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291800&stc=1[/IMG]

Now, the installation of discover was made through the command 

```

sudo apt install plasma-discover

```

if I remember correctly, and seemed to have generated some errors that I couldn't solve, among which, the following:

```

kf.kirigami: Warning: Theme implementations should use Kirigami.BasicThemeDefinition for its root item
kf.kirigami: Failed to find a Kirigami platform plugin

```

This Kirigami seems to be used only in Android mobile applications and not suitable for desktop, and in any case, I couldn't find any installable package.
Anyone has any idea of what could have happened and can help me?

I will try to provide any needed infromation but please, explain anything I should do to obtain them, still a complete noob with this #-o

Thanks so much for helping.

Alex

---

### Post by guiverc on 2023-02-16
You mention *noob *so I'll give some of my thoughts..

I have no idea what `goverlay` is/was; a CLI enquiry though found it and reported `goverlay | 0.7.1-2 | jammy/universe   | source, amd64, arm64, armhf, ppc64el` ([https://packages.ubuntu.com/jammy/goverlay](https://packages.ubuntu.com/jammy/goverlay)).  To look up details I tend to rely on `apt-cache search`, `snap search` and `rmadison`  (*the last one as most people aren't using the release I'm using* *& `apt-cache` shows for my release*)

I've seen "kf.kirigami" before (*but remember little*); assume KF = KDE Frameworks, & quickly search online so
- [https://github.com/KDE/kirigami](https://github.com/KDE/kirigami)
- [https://api.kde.org/frameworks/kirigami/html/index.html](https://api.kde.org/frameworks/kirigami/html/index.html)

I also wonder given it's appearing as BLACK if it relates to *dark theming*, and thus wonder if `kvantum` will help you.. Theming isn't my strong suit, but I know it's mentioned many times at Lubuntu's discourse; a quick search finds one entry (*it maybe useful?*)

- [https://discourse.lubuntu.me/t/20-04-contribution-manual-to-customize-lxqt-and-different-color-schemes-for-breeze/992](https://discourse.lubuntu.me/t/20-04-contribution-manual-to-customize-lxqt-and-different-color-schemes-for-breeze/992)

i believe I grabbed & used that link (*of the number in my search*) as I recognized "Breeze" in the title; and recalled seeing Breeze in the *depends* in my first linked URL (ie. `goverlay` details).

If you'd like me to look further, can you please run `neofetch --off`  and paste the results; also please tell me what Qt Style you're using ([*open appearance in LXQt settings*]("https://manual.lubuntu.me/lts/3/3.2/3.2.2/appearance.html")), as then I'll boot a *jammy* (22.04)system & see if I get issues when I match the themes to what you have, and I can explore further. I'm not interested in your machine specs, just the theming detail...

---

### Post by alexis0b on 2023-02-19
I thank you very much for your help and sorry for answering so late, actually I couldn't see your answer cause I had additional problems to the system and so I decided to do what I was already planning to do: change Linux distribution.
I've installed Manjaro and I'm very satisfied with it so far, and obviously the problem is not there anymore.
Sorry for all the effort you spent in looking through my problem and thank you for your kindness.
I guess I should solve this thread and maybe your answer could help others with the same issue.

Thanks a lot

---

