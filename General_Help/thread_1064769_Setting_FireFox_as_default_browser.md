---
title: "Setting FireFox as default browser"
date: 2009-02-09
forum: General Help
---

### Post by MeLight on 2009-02-09
Hi,
I've installed Opera a few days ago, it's all good, but I still want firefox as my deafult browser, where do I set this feature? Thanx

---

### Post by ibutho on 2009-02-09
Go to System -> Preferences and look for "Preferred Applications". You can use that tool to setup your default browser and mail client.

---

### Post by DarkTxS on 2009-02-09
You can also do this:
Open your FireFox browser -> Edit -> Preferences -> Choose Tab "Advanced" -> See "System Defaults" and click on "Check Now". Now you can set the FireFox as your default browser.

---

### Post by MeLight on 2009-02-09
Ok, checked both through FireFox and through preferred applications. The weird thing is they both say that FF is my default browser, but when I open a web page from other applications Opera opens instead of FF, any thoughts?

---

### Post by mb_webguy on 2009-02-09
Setting Firefox as your default web browser in Preferred Applications *should* automatically associate Firefox with html files, but if not you can try doing it manually.

Save an html file to your computer, then right-click on the file and select Properties.  On the Open With tab, select Firefox.

---

### Post by photon_man62 on 2009-02-09
> **MeLight said:**
> Ok, checked both through FireFox and through preferred applications. The weird thing is they both say that FF is my default browser, but when I open a web page from other applications Opera opens instead of FF, any thoughts?

If it happens on only 1 application, it may be the application ITSELF. Like Steam on Windows ALWAYS opens in IE instead of the default browser, or Gadu-Gadu (an IM) always opens up in Firefox instead of Opera, for example.

You can try setting the default in the Opitions/Preferences of the program itself.

---

### Post by Daxxi on 2010-11-23
I found the solution I wanted at > [this link]("http://www.simplehelp.net/2009/05/07/how-to-change-the-default-web-browser-in-ubuntu/") <.

**[B]sudo update-alternatives --config x-www-browser**
[/B]
"/usr/bin/x-www-browser" is an alias for your default browser, so it can be used at the terminal or in .desktop entries as the Exec key or in the launcher menu.

e.g. this command opens an html file in Firefox, for me:
x-www-browser /usr/share/doc/cmake-docs/cmake.html

See also the man page:
[B]man update-alternatives


[/B]

---

