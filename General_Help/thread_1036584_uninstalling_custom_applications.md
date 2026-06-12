---
title: "uninstalling custom applications"
date: 2009-01-11
forum: General Help
---

### Post by zoomiest on 2009-01-11
This sounds trivial, but I have searched for the answer and can't find it...

I have installed a couple of custom-compiled applications on my Ubuntu server 8.10 - full command line... and now I want to uninstall two of them...

I am well acquainted with:
```
sudo apt-get remove [packagename]
```

and particularly liked [this article]("http://www.cyberciti.biz/faq/howto-delete-remove-software-using-apt-get-command/").

However, the applications that I need to uninstall are not listed with

```
dpkg --list
```

What is my next step? Delete the directories?

(Background: its a couple of indexing tools for MySQL: Sphinx and Sphinx_for_Cats)

---

### Post by tuxxy on 2009-01-11
Locate the specific apps directory and list the files as there is more than likely an uninstall script in there that needs running.

---

