---
title: "Launchers - security threat ?"
date: 2010-02-27
forum: Desktop Environments
---

### Post by lucasart on 2010-02-27
Hello

I just realized that on a technical level, launchers are not equivalent to symbolic links (created by means of ln -s command).
My question is simply: **why do launchers exist ?** I've also read that they are the best way to get (stupid) users to execute files that they've downloaded from email attachment. This is the main open door to any trojan attack, which -even without root powers- can be devastating (and if cleverly done may even get root powers ultimately).

Thank you

PS: I use Gnome and not KDE, but I believe KDE has the same security hole.

---

### Post by mcduck on 2010-02-27
well, a link to a program's binary would only be able to launch that program (if you have set your file manager to run executable files when clicked), but it wouldn't allow you to give any options or parameters when launching the program. So you need something that is able to launch more complicated commands, a launcher.

Not to mention that launcher's also include a  lot more information, like an icon, description, and a human-readable name ("Open Office Writer-read and write text documents" and OpenOffice icon, versus "oowriter" and a generic program icon).

Of course if you are happy doing most of things from command-line you don't need launchers, but if you prefer using a graphical desktop you'll always run into some type of launchers, be it on your desktop or panel, or in menus. And this applies to all operating systems.

In the trojan case you mentioned I wouldn't say that the launchers are the security hole, the user is. All trojans are simply based on user stupidity, and there really is no working way to protect against them other than fixing the user's behavior. As long as the user mindlessly executes files and commands from strange and untrustworthy sources there is _always_ a way to fool that user to do something that will damage the suer's files.

---

### Post by gadolinio on 2010-02-27
> **mcduck said:**
> well, a link to a program's binary would only be able to launch that program (if you have set your file manager to run executable files when clicked), but it wouldn't allow you to give any options or parameters when launching the program. So you need something that is able to launch more complicated commands, a launcher.

Not to mention that launcher's also include a  lot more information, like an icon, description, and a human-readable name ("Open Office Writer-read and write text documents" and OpenOffice icon, versus "oowriter" and a generic program icon).

Of course if you are happy doing most of things from command-line you don't need launchers, but if you prefer using a graphical desktop you'll always run into some type of launchers, be it on your desktop or panel, or in menus. And this applies to all operating systems.

In the trojan case you mentioned I wouldn't say that the launchers are the security hole, the user is. All trojans are simply based on user stupidity, and there really is no working way to protect against them other than fixing the user's behavior. As long as the user mindlessly executes files and commands from strange and untrustworthy sources there is _always_ a way to fool that user to do something that will damage the suer's files.

HAHAHA excellent reply... I completely agree!!

---

