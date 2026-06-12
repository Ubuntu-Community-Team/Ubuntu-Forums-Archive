---
title: "How do I install those other settings into KDE 'systemsettings'"
date: 2015-04-06
forum: Desktop Environments
---

### Post by MiroJanosik on 2015-04-06
Hi, I need to edit KDE "sound notifications" settings but I don't see it in the settings.

I am on XUbuntu (XFCE) and I use Krusader (KDE file browser) which has sound notifications on various actions. In section [http://www.krusader.org/documentation/faq_usage.html#faqu_sound](http://www.krusader.org/documentation/faq_usage.html#faqu_sound) I found that it should be edited in KDE settings:

*"Those are the default KDE System sounds, and not related to Krusader. If you want to disable them globally open your KDE System Settings ( systemsettings): Application Appearance and Behavior &#8594; Application and System Notifications &#8594; Manage Notifications, Event Source: "KDE Workspace" and uncheck sound items you do not like."*

I did not have 'systemsettings' installed on my fresh XUbuntu 15, so I installed it. Running it showed me only icon to edit "Desktop behavior" and there is nothing else. How do I install those other settings into 'systemsettings'?

-- edit --
I have a pre-release daily build of XUbuntu 15.04. I found a 'hack' workaround - inspired by system where notifies are disabled. I created a file "~/.kde/share/config/knotifyrc" with content:
[I][Sounds]
No sound=true[/I]

And it works. But still I would like to know how to solve it in a nice way.

---

### Post by brunces on 2015-06-19
Hey, MiroJanosik.

I guess I have a similar problem here...

Every time I install Ubuntu, I also install Clementine and K3B. Then, I install the KDE System Settings, following this tutorial...

[http://www.webupd8.org/2011/04/make-kde-applications-look-native-in.html](http://www.webupd8.org/2011/04/make-kde-applications-look-native-in.html)

... so I can make my KDE programs use the same GTK theme I use as default for the whole system (Numix). Everything works great.

Now that I'm using Xubuntu 15.04, I did the same (installed Clementine, K3B and the KDE System Settings), however, when I launch the KDE System Settings, the window appears empty, I mean, without any icons (see the screenshot attached, please).

[ATTACH=CONFIG]262712[/ATTACH]

I already have the "Launch KDE services on startup" option marked in Sessions and Startup.

Do you know what might be happening here? How can I fix this? Isn't KDE System Settings supposed to work with XFCE? Please, if possible, help me fix this; or tell me where I can get help for this, if not here.

Thanks for your time. I appreciate it. :)

brunces

---

