---
title: "Firefox Language Packs"
date: 2009-01-14
forum: General Help
---

### Post by nvikram on 2009-01-14
Hello,

I am on ubuntu 8.10 and have all the updates installed for firefox through the update manager. I realize that ubuntu comes with the en-GB firefox language pack installed by default. It is fine for now, but is there anyway for me to install the en-US language pack?

Thanks,
Vikram

---

### Post by gettinoriginal on 2009-01-14
Firefox > Edit > Preferences > Content > Languages > Choose   :P

---

### Post by mister_playboy on 2009-05-22
You simply need to disable/remove all other language packs to have en-US... it can't be downloaded separately.

Only root can remove language packs... a normal user can only disable them.  To get rid of en-GB, Run Firefox as root from a terminal:

```
sudo firefox
```

Then go to Tools > Add-ons > Language Packs and uninstall both en-GB extensions.

Running as root will cause root to take ownership of some of your config files and break Firefox for your normal user.  To reclaim them, take ownership of the folder in ~/.mozilla/firefox... on my computer, this is called 93p7wwjw.default.  The example using my info would be:

```
cd ~/.mozilla/firefox

sudo chown -R $USER:$USER 93p7wwjw.default/
```

This should solve your problems!  ):P

---

### Post by firesock on 2010-04-18
> **mister_playboy said:**
> You simply need to disable/remove all other language packs to have en-US... it can't be downloaded separately.

Only root can remove language packs... a normal user can only disable them.  To get rid of en-GB, Run Firefox as root from a terminal:

```
sudo firefox
```

Then go to Tools > Add-ons > Language Packs and uninstall both en-GB extensions.

Running as root will cause root to take ownership of some of your config files and break Firefox for your normal user.  To reclaim them, take ownership of the folder in ~/.mozilla/firefox... on my computer, this is called 93p7wwjw.default.  The example using my info would be:

```
cd ~/.mozilla/firefox

sudo chown -R $USER:$USER 93p7wwjw.default/
```

This should solve your problems!  ):P

Thank you!! just run firefox with sudo

;)

---

