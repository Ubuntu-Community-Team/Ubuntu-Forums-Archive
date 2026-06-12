---
title: "Some GTK apps look weird"
date: 2013-03-29
forum: Desktop Environments
---

### Post by hydrargyrum on 2013-03-29
Hi all!

First, I must mention that I use [Netrunner]("http://netrunner-os.com") (which is based on Kubuntu 12.10) but not Kubuntu itself. The differencies are, from my experience, minimal (I can be wrong). The most significant difference that is related to my question is that Netrunner uses new GTK appearance module for systemsettings, the same as in Kubuntu 13.04.

*This post is almost a copy of the same post from Netrunner forums, I haven't got any valuable information from there.*

**The problem:** it seems that some of GTK apps (probably GTK3-based) do not react on GTK theme changing via Systemsettings (see screenshot attached for Geary Mail).

[ATTACH=CONFIG]240677[/ATTACH]

**My expectation:** all apps should look uniformly.

Also, I've realized that GTK open file window in some apps does not match the Oxygen icon theme (see screenshot attached for GIMP).

[ATTACH=CONFIG]240679[/ATTACH]

I have Kubuntu 12.10 as another installation on the same computer, and it has no such issues. For years, I just changed GTK theme via systemsettings and everything worked. Also, I don't see this issue in Kubuntu 13.04 Beta under VirtualBox.

Below are my obvervations.

I've found that under gnome-control-center -> Appearance, there are no GTK themes in list to select (see screenshot attached). As far as I know, these themes are GTK3 ones, so probably something is broken for GTK3.

[ATTACH=CONFIG]240678[/ATTACH]

Also, under newly created user in Netrunner I have the same issues, so probably this isn't connected to some broken configs in my home folder.

I've found that fonts under Firefox also look strange (see another screenshot attached).

[ATTACH=CONFIG]240680[/ATTACH]

I've also discovered that appearance of some GTK apps, such as Firefox becomes to look well after gnome-settings-daemon started. 


I will be grateful for any help.

Thanks.

---

### Post by rdettogni on 2013-03-29
I had some problems with GTK theme consistency after enabling SNA Intel video acceleration. I did the workaround changing the Xorg.conf file. Just deleting the file that I created solved the problem.

---

### Post by hydrargyrum on 2013-03-29
Have you saved previous file? If yes, can you please post diff somewhere?

---

