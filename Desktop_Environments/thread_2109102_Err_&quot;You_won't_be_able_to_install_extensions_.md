---
title: "Err: &quot;You won't be able to install extensions from https://extensions.gnome.org&quot;"
date: 2013-01-26
forum: Desktop Environments
---

### Post by GnuKian on 2013-01-26
[COLOR=Red][COLOR=Black]EDIT: This is solve[/COLOR][/COLOR]d!
It was because of ignoring an notification from firefox that it announced to active all plugin!

_______________________________________________
[COLOR=Red][COLOR=Black]I've installed Gnome-shell using this commands:[/COLOR][/COLOR]

```
sudo apt-get install gnome-shell
sudo apt-get install ubuntu-gnome-desktop
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-gnome-default-settings
sudo apt-get install gnome-tweak-tool
```It was working and I could install extention via [https://extensions.gnome.org/](https://extensions.gnome.org/), So I activated this extentions:
User Theme: [https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)
Temperature: [https://extensions.gnome.org/extension/82/cpu-temperature-indicator/](https://extensions.gnome.org/extension/82/cpu-temperature-indicator/)
Net speed: [https://extensions.gnome.org/extension/104/netspeed/](https://extensions.gnome.org/extension/104/netspeed/)
Media player: [https://extensions.gnome.org/extension/55/media-player-indicator/](https://extensions.gnome.org/extension/55/media-player-indicator/)

After a restart I get the below error at the top of [Gnome extensions site]("https://extensions.gnome.org/").  This error prevents installing new features from the site!
[COLOR=Red]You do not appear to have an up to date version of GNOME3. You won't be able to install extensions from here. See the [about page]("https://extensions.gnome.org/about/#old-version") for more information.[/COLOR]

**More details**:
1. Mozilla "Gnome Shell Integration" plugin is enable.
2. Out put of "[FONT=Courier New]apt-cache policy gnome-shell[/FONT]" command is:
```
gnome-shell:
  Installed: 3.6.2-0ubuntu0.2
  Candidate: 3.6.2-0ubuntu0.2
  Version table:
 *** 3.6.2-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     3.6.1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe i386 Packages
```3. I deleted all folders from the below direction and then I powered of the system. It didn't solve the problem.
```
~/.local/share/gnome-shell/extensions
```

---

