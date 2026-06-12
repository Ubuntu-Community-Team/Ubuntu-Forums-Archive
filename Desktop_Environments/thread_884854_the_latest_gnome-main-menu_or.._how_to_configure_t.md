---
title: "the latest gnome-main-menu or.. how to configure the one we have"
date: 2008-08-09
forum: Desktop Environments
---

### Post by bp1509 on 2008-08-09
d

---

### Post by motang on 2008-08-10
I would like to know myself.  As the one in Hardy is the same one that has been in Ubuntu for years now.  I did find out that Intrepid has a newer version and I downloaded Alpha 3 but I can't seem to install it as it conflicts with some other package and even Synaptic errors out.  

I hope someone would have some good input on this issue.

---

### Post by jrhorner on 2008-10-25
I'm new at this too but I had some luck changing the following section in file /usr/share/gnome-main-menu/system-items.xbel

<bookmark href="package-manager.desktop" added="2007-01-16T05:53:36Z" modified="2007-01-16T05:53:36Z" visited="2007-01-16T05:53:36Z">
<info>
<metadata owner="http://freedesktop.org">
<mime:mime-type type="application/x-desktop"/>
<bookmark:groups>
<bookmark:group>rank-2</bookmark:group>
</bookmark:groups>
<bookmark:applications>
<bookmark:application name="Install Software" exec="/usr/bin/gnome-app-install" timestamp="1168926816" count="1"/>
</bookmark:applications>
</metadata>
</info>
</bookmark>

to the following

<bookmark href="gnome-app-install.desktop" added="2007-01-16T05:53:36Z" modified="2007-01-16T05:53:36Z" visited="2007-01-16T05:53:36Z">
<info>
<metadata owner="http://freedesktop.org">
<mime:mime-type type="application/x-desktop"/>
<bookmark:groups>
<bookmark:group>rank-2</bookmark:group>
</bookmark:groups>
<bookmark:applications>
<bookmark:application name="Add/Remove Software" exec="/usr/bin/gnome-app-install" timestamp="1168926816" count="1"/>
</bookmark:applications>
</metadata>
</info>
</bookmark>

It may not be synaptic but you can use the same concept to add it.
I used sudo gedit in terminal to change it.

---

