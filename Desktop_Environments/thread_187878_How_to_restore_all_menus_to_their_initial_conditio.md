---
title: "How to restore all menus to their initial condition?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Dralt on 2006-06-03
OK...classic story I guess...

I installed kubuntu-desktop to give it a try.

I didn't like it.

I uninstalled all packages that were installed while installing kubuntu-desktop.

Alas, there are left-over menu entries everywhere.

How can I get back to the default menus you get after installing Ubuntu?

I supposed there are a number of files I should edit or whack. Where are they?

---

### Post by aysiu on 2006-06-03
Try these commands: ```
mv ~/.gconf/apps/gnome-settings/alacarte/%gconf.xml ~/.gconf/apps/gnome-settings/alacarte/%gconf_old.xml
killall gnome-panel
```

---

### Post by Dralt on 2006-06-03
Thanks, I am going to try this.

---

### Post by Dralt on 2006-06-03
This file does not contain any menu information, how would removing it fix anything?

---

### Post by aysiu on 2006-06-03
[QUOTE=Dralt]This file does not contain any menu information, how would removing it fix anything?[/QUOTE] It contains information for me: ```
cat ~/.gconf/apps/gnome-settings/alacarte/%gconf.xml
<?xml version="1.0"?>
<gconf>
        <entry name="history-998" mtime="1149303990" type="list" ltype="string">
                <li type="string">
                        <stringvalue>/opt/thunderbird/icons/mozicon50.xpm</strin gvalue>
                </li>
                <li type="string">
                        <stringvalue>/opt/thunderbird/icons</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>/usr/share/pixmaps/mozilla-thunderbird-menu .png</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>/opt/firefox/icons/mozicon128.png</stringva lue>
                </li>
                <li type="string">
                        <stringvalue>/opt/firefox/icons</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>/usr/share/pixmaps/mozilla-firefox.png</str ingvalue>
                </li>
        </entry>
</gconf>
``` As far as I can tell most config files contain information only if you've modified the original config file that lives in /etc somewhere.

If you didn't manually add in those "extra" entries, they're standard entries, and you'll have to remove them manually.

---

