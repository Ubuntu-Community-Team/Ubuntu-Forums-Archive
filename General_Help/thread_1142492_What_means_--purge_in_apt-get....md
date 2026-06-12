---
title: "What means --purge in apt-get..."
date: 2009-04-29
forum: General Help
---

### Post by rado3105 on 2009-04-29
What means --purge in:
sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin

it clears all dependencies?

---

### Post by _Purple_ on 2009-04-29
purge
           purge is identical to remove except that packages are removed and purged.

--purge
           Use purge instead of remove for anything that would be removed. An asterisk ("*") will be displayed next to packages which are scheduled to be purged. Configuration Item: APT::Get:: Purge.

```
man apt-get
```

---

### Post by kpkeerthi on 2009-04-29
To clear the unused dependencies use
```
sudo apt-get autoremove
```

or use deborphan (google for more info)

---

