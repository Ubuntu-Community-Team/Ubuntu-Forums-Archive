---
title: "Unable to install Gnome 3 extensions"
date: 2013-02-09
forum: Desktop Environments
---

### Post by cyanide911 on 2013-02-09
I'm on Ubuntu 12.04 with Gnome 3.4 added via the Gnome ppa.

It's running well, but I'm not able to install extensions via the extensions.gnome.org website. I've tried it in both Firefox and Chromium. The Gnome plugin is installed in both the browsers, I've checked.

If I open a page for any extension, and click on the OFF-ON slider (which is on OFF), it slides to ON position. But nothing happens after that. I don't see any changes reflected. 


How do I debug this?

---

### Post by Frogs Hair on 2013-02-09
3.4 is the version that comes in the software center. What is different about the PPA ? and are you sure it is 3.4 

The extensions work fine with the Gnome Shell version in the software center.

---

### Post by cyanide911 on 2013-02-10
> **Frogs Hair said:**
> 3.4 is the version that comes in the software center. What is different about the PPA ? and are you sure it is 3.4 

The extensions work fine with the Gnome Shell version in the software center.

No I don't think anything is different about the PPA (I just mentioned it) and yeah it's 3.4.1.

---

### Post by PhilGil on 2013-02-10
Does the extension download from the site after you move the slider? You should still get a dialog box asking if you want to download the extension. Perhaps you have another add-on preventing the download from initiating.

If it downloads, does the extension appear in Gnome Tweak Tool? Sometimes you need to activate it using the tweak tool, as well.

Some extensions also require a shell restart after they're installed...
```
ALT+F2
Type "r" in the command text box
Press ENTER
```

---

### Post by cyanide911 on 2013-02-10
> **PhilGil said:**
> Does the extension download from the site after you move the slider? You should still get a dialog box asking if you want to download the extension. Perhaps you have another add-on preventing the download from initiating.

If it downloads, does the extension appear in Gnome Tweak Tool? Sometimes you need to activate it using the tweak tool, as well.

Some extensions also require a shell restart after they're installed...
```
ALT+F2
Type "r" in the command text box
Press ENTER
```

Absolutely nothing happens when I move the slider. It slides from OFF to ON, that's it. Then if I reload the page, I see it at OFF again. 

Restarting the shell does nothing, and the extension doesn't appear in the Gnome tweak tool either.

---

### Post by Frogs Hair on 2013-02-10
Script blocking browser extensions may interfere with the ability to install extensions.  Could please post a link to the PPA.

---

### Post by cyanide911 on 2013-02-10
Firefox is completelty bare-bones so I don't think it's anything to do with that.

[http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/](http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/)

I followed this guide, so the ppa is ppa:gnome3-team/gnome3

---

### Post by PhilGil on 2013-02-10
Is it just the website you're having trouble with? Can you install extensions manually or from a ppa?

---

### Post by Frogs Hair on 2013-02-10
When you select on you should get a message as below. 

 _Important_ On the shell extensions page select compatible with current version above the displayed extensions

---

### Post by cyanide911 on 2013-02-11
> **PhilGil said:**
> Is it just the website you're having trouble with? Can you install extensions manually or from a ppa?



Yeah I'm able to install extensions manually. And they do reflect on the extensions.gnome.org/local. But I can't uninstall them from there. 
But strangely I can turn them on and off from the website...

> **Frogs Hair said:**
> When you select on you should get a message as below. 

 _Important_ On the shell extensions page select compatible with current version above the displayed extensions

Yeah it's already at compatible with current version. I don't get any such message :(

---

### Post by PhilGil on 2013-02-11
> **cyanide911 said:**
> Yeah I'm able to install extensions manually. And they do reflect on the extensions.gnome.org/local. But I can't uninstall them from there. 
But strangely I can turn them on and off from the website...
You've got me stumped. Have you been following [this thread]("http://askubuntu.com/questions/142054/why-does-installing-gnome-shell-extensions-from-extensions-gnome-org-fail-silent") on Ask Ubuntu? Doesn't sound like you're the only one having problems, and there are several possible fixes suggested there.

---

