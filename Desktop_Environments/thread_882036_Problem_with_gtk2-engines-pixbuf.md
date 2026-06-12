---
title: "Problem with gtk2-engines-pixbuf"
date: 2008-08-06
forum: Desktop Environments
---

### Post by Dirty Soap on 2008-08-06
Okay, so earlier today, I installed Compiz-Fusion and everything went fine. Then I installed a new gnome theme. And it didn't install like it should have, like I didn't have gtk2-engines-pixbuf installed. However, I did.

So I went to synaptic and tried to reinstall gtk2-engines-pixbuf, but the option was grayed out, so I removed it so I could newly install it. And here's where my problem came up. It wouldn't let me install gtk2-engines-pixbuf. I got this error message:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gtk2-engines-pixbuf: Depends: libgtk2.0-0 (= 2.12.0-1ubuntu3) but 2.12.0-1ubuntu3.1 is to be installed
E: Broken packages

```

Turns out I have libgtk2.0-0_2.12.0-1ubuntu3.1 (not 2.12.0-1ubuntu3). And I can't install libgtk2.0-0_2.12.0-1ubuntu3 because I already have the latest version (which is ubuntu3.1) and gtk2-engines-pixbuf needs the ubuntu3 version to install.

So I'm stuck with crappy looking gnome themes. 

Is there anything I can do? Thanks for your help.

---

