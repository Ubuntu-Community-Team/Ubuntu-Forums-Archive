---
title: "Upgrading to Firefox 1.5.1 under Hoary"
date: 2006-03-31
forum: Desktop Environments
---

### Post by bpont on 2006-03-31
I've discovered that I can't install any extensions (Mozilla won't allow it due to 'security issues') unless I upgrade from the default Ubuntu Hoary Firefox version 1.0.2.  I read: [COLOR="Red"][https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")[/COLOR] which offers instructions on how to install the latest Firefox, but it's meant for the Breezy release.

So my question is: do the instructions at: [COLOR="Red"][https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")[/COLOR] apply equally true for the Hoary computer users such as myself or is there a slightly different page someplace else with different instructions for Hoary users?

---

### Post by art on 2006-03-31
I think it should work on hoary.

---

### Post by aysiu on 2006-03-31
Should work just fine for Hoary.

The only difference I know of is Firefox being called *mozilla-firefox* in Hoary and *firefox* in Breezy, but I think even that the Wiki covers.

---

### Post by bpont on 2006-03-31
[QUOTE=aysiu]Should work just fine for Hoary.

The only difference I know of is Firefox being called *mozilla-firefox* in Hoary and *firefox* in Breezy, but I think even that the Wiki covers.[/QUOTE]

Thanks Aysiu...I searched the forum and came across the Firefox 1.5 install script you posted.  Was thinking of using it...but wanted to make sure the naming conventions (i.e. mozilla-firefox vs. firefox) didn't need to be edited first since I use Hoary and not Breezy.  Also, not sure if I'll need to create an /opt folder or whether it already exists for Hoary (will have to check when I get home).  Obviously, your script wouldn't work if /opt was not there.

---

### Post by aysiu on 2006-03-31
[QUOTE=bpont]Thanks Aysiu...I searched the forum and came across the Firefox 1.5 install script you posted.  Was thinking of using it...but wanted to make sure the naming conventions (i.e. mozilla-firefox vs. firefox) didn't need to be edited first since I use Hoary and not Breezy.  Also, not sure if I'll need to create an /opt folder or whether it already exists for Hoary (will have to check when I get home).  Obviously, your script wouldn't work if /opt was not there.[/QUOTE] It can't hurt to just try to make an /opt folder. If it exists, this is what will happen: ```
bpont@ubuntu:~$ sudo mkdir /opt
Password:
mkdir: cannot create directory `/opt': File exists
``` And, I double-checked the script--it links to both /usr/bin/mozilla-firefox *and* /usr/bin/firefox, so it should be good for Hoary.

If it doesn't work... well, there's always the uninstall script...

---

