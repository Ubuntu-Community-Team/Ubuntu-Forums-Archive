---
title: "I cant install Gnome-shell extensions using Opera browser. Why?"
date: 2012-10-19
forum: Desktop Environments
---

### Post by glaubersm on 2012-10-19
Hello
I use Ubuntu Gnome Remix 12.10 and I cant install Gnome-shell extensions using Opera browser because the ON/OFF button is not available on Gnome extensions website. Why? Is it a Gnome plug-in incompatibility/bug?

Test here [https://extensions.gnome.org/](https://extensions.gnome.org/) please.

---

### Post by PaulW2U on 2012-10-19
You need to use Firefox.

---

### Post by glaubersm on 2012-10-19
> **PaulW2U said:**
> You need to use Firefox.

I know, but Opera is my default browser and I dont want open FF only to install GS extensions.
Why Gnome plug-in works only with FF? Bug or intentional?

---

### Post by PaulW2U on 2012-10-19
> **glaubersm said:**
> Why Gnome plug-in works only with FF? Bug or intentional?

Intentional, it's always been that way. I believe Opera doesn't understand the format of an extension so can't deal with it.

---

### Post by glaubersm on 2012-10-19
> **PaulW2U said:**
> Intentional, it's always been that way. I believe Opera doesn't understand the format of an extension so can't deal with it.

Opera dev says
> The problem is a non-working browser plugin, not an Opera problem

[https://extensions.gnome.org/about/](https://extensions.gnome.org/about/)

"Note: there were some bugs in the browser plugin shipped in some versions of GNOME 3.2 that prevent it from working properly under WebKit-based browsers like Epiphany and Chromium. GNOME Shell 3.2.2.1 has fixed these problems, so make sure you are using it."

They don't mention Opera but I would assume it is the same.

From: [http://my.opera.com/ruario/blog/show.dml/53705022#comment98302962](http://my.opera.com/ruario/blog/show.dml/53705022#comment98302962)

---

### Post by RavisPohan on 2012-10-21
Works fine with Epiphany here, so it's not *just* for firefox.

---

### Post by glaubersm on 2012-10-21
Yes, but Opera is my default browser and Gnome plug-in is not compatible with it. :(

---

### Post by Frogs Hair on 2012-10-21
Hello glaubersm, 

I just tested extension installation with Opera 12.02 and the extension installed with out any problems. If you are using any script or ad blocking software you may want to disable it and restart Opera before trying to install any extensions. I am running Ubuntu 12.10.

Edit: Many of the extensions have been updated for Gnome 3.6 which I am using so that may be part of the problem. There may be an extension compatibility work around if that is the problem.

---

### Post by glaubersm on 2012-10-21
> **Frogs Hair said:**
> Hello glaubersm, 

I just tested extension installation with Opera 12.02 and the extension installed with out any problems. If you are using any script or ad blocking software you may want to disable it and restart Opera before trying to install any extensions. I am running Ubuntu 12.10.

Edit: Many of the extensions have been updated for Gnome 3.6 which I am using so that may be part of the problem. There may be an extension compatibility work around if that is the problem.

I found the problem here!
Opera has a feature to enable plug-ins only on demand. After disable this feature I can install Gnome-shell extensions using Opera!
You can disable it in Opera preferences or in site preferences.

first option:
press ctrl+f12
select "advanced" tab
on left side select "Content"
uncheck "Enable plug-ins only on demand"

second option:
press f12
select "edit site preferences"
select "Content" tab
uncheck "Enable plug-ins only on demand"

Done!
You can install GS extensions now. \\:D/

Thanks for your help, guys!

---

