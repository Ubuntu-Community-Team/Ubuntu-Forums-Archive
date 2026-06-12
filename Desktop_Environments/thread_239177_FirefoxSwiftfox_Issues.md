---
title: "Firefox/Swiftfox Issues"
date: 2006-08-18
forum: Desktop Environments
---

### Post by fatsheep on 2006-08-18
I'm having a few issues in firefox/swiftfox, nothing major but I just thought I'd check if anyone else is experiencing them:

1.  The "open" button for downloaded files doesn't work.
2.  You cannot drag and drop bookmarks unless you go into the bookmarks manager.
3.  Plugins don't automatically install (I'm assuming this is normal but maybe not?).
4.  The "open containing folder" button for downloaded files doesn't work.
5.  Even though I have installed Java Runtime Environment, some applets such as chessanytime.com and IRC chatrooms don't work and tell me that I need to install JRE even though I already have it.

---

### Post by fatsheep on 2006-08-18
Is anyone else experiencing these problems?

---

### Post by ubu-for on 2006-11-23
Yes. I use the Java RE for Firefox, too, but Swiftfox (installer version) can't find the plugin.

THX for your HELP!

---

### Post by ubu-for on 2007-01-10
> **ubu-for said:**
> Yes. I use the Java RE for Firefox, too, but Swiftfox (installer version) can't find the plugin.

THX for your HELP!

Solution:

1. Install Automatix: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

2. Install with Automatix Swiftfox (1.5.0.7) and the Swiftfox Plugins.

3. Install Swiftfox 2.0.0.1: [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm)

4. Go to "opt/swiftfox/plugins" and rename "libjavaplugin.so" and "libjavaplugin_oji.so" to "libjavaplugin.so.OLD" and "libjavaplugin_oji.so.OLD".

5. Go to "opt/swiftfox.old/plugins" and copy the link "libjavaplugin_oji.so" and paste to "opt/swiftfox/plugins".

6. Start Swiftfox and go to: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) :mrgreen:

---

### Post by stillingen on 2007-01-19
Alternatively for plugins - make a symlink from swiftfox's plugin directory to Firefox's plugins directory. This worked for me

1.Rename Swiftfox's plugin directory sudo mv /opt/swiftfox/plugins /opt/swiftfox/pluginsOld
2.Make a symlink to to Firefox's plugin directory sudo ln -s /usr/lib/firefox/plugins /opt/swiftfox/
3.Restart Swiftfox, and verify with about:plugins

I'm using Dapper 2.6.15-27-386

---

### Post by wilberfan on 2007-03-18
> **stillingen said:**
> Alternatively for plugins - make a symlink from swiftfox's plugin directory to Firefox's plugins directory. This worked for me

1.Rename Swiftfox's plugin directory sudo mv /opt/swiftfox/plugins /opt/swiftfox/pluginsOld
2.Make a symlink to to Firefox's plugin directory sudo ln -s /usr/lib/firefox/plugins /opt/swiftfox/
3.Restart Swiftfox, and verify with about:plugins

I'm using Dapper 2.6.15-27-386

Ah....worked beautifully!   :guitar:

---

