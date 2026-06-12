---
title: "Getting second firefox installation to use plugins/extensions from the first"
date: 2009-06-09
forum: General Help
---

### Post by RedACE on 2009-06-09
I have been using the installation of firefox that comes with Ubuntu and have several extensions and plugins configured with it. However, I've found that this ubuntu-ized version of firefox doesn't like certain java applications and will just freeze when it tries to load them. I've installed another copy of firefox manually to /usr/local/firefox and it can handle these java apps fine.

What I'd like to do is get this new version of firefox to use all the extensions and plugins that I have installed in the ubuntu-ized instance of firefox. In particular, I'm trying to get the adobe flash plugin working. How can I point firefox towards the plugin that's already installed?

---

### Post by yonyz on 2009-06-09
You can use the FEBE Firefox extension ([https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)) to create a backup of your Firefox addons and/or preferences and import it to your other installation of Firefox.

---

### Post by RedACE on 2009-06-09
> **yonyz said:**
> You can use the FEBE Firefox extension ([https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)) to create a backup of your Firefox addons and/or preferences and import it to your other installation of Firefox.

All of my extensions are loaded, since both copies of firefox are picking up my profile in ~/.mozilla. Just the plugins aren't loading the new version. 

I tried FEBE but it doesn't seem to have an option to back up the plugins. My understanding of how plugins work is they're installed elsewhere on the system and firefox just references them. I just don't know how to make the second copy of firefox use the plugins I have.

---

### Post by yonyz on 2009-06-10
Try this:
[http://kb.mozillazine.org/Move_plugins_to_another_location_-_Firefox](http://kb.mozillazine.org/Move_plugins_to_another_location_-_Firefox)

---

### Post by RedACE on 2009-06-11
> **yonyz said:**
> Try this:
[http://kb.mozillazine.org/Move_plugins_to_another_location_-_Firefox](http://kb.mozillazine.org/Move_plugins_to_another_location_-_Firefox)

This was helpful, thank you.

---

