---
title: "Chromium doesn't have gnome-shell-integration plugin installed"
date: 2014-05-03
forum: Desktop Environments
---

### Post by reuben3 on 2014-05-03
I can't install extensions from chromium, because the gnome-shell-extensions plugin is completely absent in chromium (about:plugins) on my system (I installed gnome-desktop from a base lubuntu install; perhaps it's missing something vital.)

I have gnome-tweak-tool installed, and appear to have all gnome-shell packages also installed.

Firefox _is_ configured with the integration; however, extension installation fails silently from firefox.

---

### Post by Frogs Hair on 2014-05-03
Script blockers such as Ghostery can effect how the Gnome Shell Extensions page works . I have never had to install anything in a browser to use the extensions page, but have had to disable script blocking. I use both Chrome and Firefox and Chrome being proprietary provides integration that I'm aware of. If you are not using an ad blocker I don't know what the problem would be. 

[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by reuben3 on 2014-05-03
Tried that, thanks, but didn't help. In about:plugins, do you see anything related to gnome? According to their site:

[COLOR=#2E3436][FONT=Cantarell]> If you are using GNOME 3.4 or newer and installation still doesn't work, check to make sure that the "GNOME Shell Integration" plugin is installed and enabled in your browser preferences. 

It's absent in chrome.[/FONT][/COLOR]

---

### Post by Frogs Hair on 2014-05-03
I installed the gnome shell again to test with and Chrome detected the integration  plugin when visiting the site and I was able to install the weather extension with Ghostery running.

---

### Post by reuben3 on 2014-05-03
I just reinstalled gnome-shell (via apt reinstall) and the plugin still isn't there when I restart chrome. I get the pink banner, but no prompt to allow integration, and about:plugins doesn't list the plugin.

---

### Post by Biber on 2014-05-21
I can confirm this bug. I have had the same install route via lubuntu and it doesn't work anymore. I had done the same for 13.10 and it worked well. Now it's gone.

---

### Post by schizosfera on 2014-05-27
i can confirm this problem too.
```
dpkg-query -L gnome-shell
``` reports ```
/usr/lib/mozilla/plugins/libgnome-shell-browser-plugin.so
``` as one of the installed files but there is no mention of chromium.

does anyone know if there is an open ticket somewhere for this issue?

---

### Post by schizosfera on 2014-05-27
for those interested, i opened a new launchpad ticket: [https://bugs.launchpad.net/ubuntu-gnome/+bug/1323734](https://bugs.launchpad.net/ubuntu-gnome/+bug/1323734)

---

### Post by RavanH on 2014-06-06
> **schizosfera said:**
> for those interested, i opened a new launchpad ticket: [https://bugs.launchpad.net/ubuntu-gnome/+bug/1323734](https://bugs.launchpad.net/ubuntu-gnome/+bug/1323734)
I can confirm both Chromium (since npapi support was dropped) and Google Chrome do not recognize the Gnome Shell Integration plugin. 

To anyone running into the same issue, ***please go to schizosfera bugreport and hit the "Does this bug affect you?" link*** at the top of the report.

The only work-around at this point seems to be to visit [http://extensions.gnome.org/](http://extensions.gnome.org/) in Firefox, Opera (faster!) or any other preferred browser.

---

