---
title: "Can't reinstall compiz after remove 4 update"
date: 2008-03-07
forum: Desktop Effects &amp; Customization
---

### Post by DXM31 on 2008-03-07
I did a search and found quit a few others that compiz stopped working after update(as well as other things but one thing at a time)

Anyway as per suggestion in the other posts I removed anything with the compiz name thru synaptic package manager, rebooted and was set to reinstall...no go
I get the message:
well I can't paste it:(

Package compiz-gnome has not available version, but exists in the database

This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of the sources.list

and my desktop is acting really wack, like I can't copy and paste, I can't drag windows around, I got not 'X' in the corner of the windows to close them...
I guess that's what I get for doing a search...
How do I get compiz back now?
Thanks

---

### Post by boeing777 on 2008-03-07
try to reload the source in synpatics

---

### Post by DXM31 on 2008-03-07
I hit the reload button still only the two options on compiz show up and still get the same error message with either one.

---

### Post by boeing777 on 2008-03-07
some people are having the exact problem as you.

most of them are fixed with this link:

[http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/](http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/)

---

### Post by DXM31 on 2008-03-07
I tried that and now I have the icons back in the corners of the windows and I can drag windows again.
when I try to activate compiz I get this message

Failed to execute child process "compiz" (No such file or directory)

and when I go to synaptic package manager I get the same old message

---

### Post by boeing777 on 2008-03-07
did you enable restricted driver for your graphic card?

---

### Post by boeing777 on 2008-03-07
sudo apt-get install compiz compiz-gnome compiz-plugins compiz-core csm

---

### Post by DXM31 on 2008-03-07
The only restricted driver I have showing is for my wifi card
Which I had to refix after the update

---

### Post by DXM31 on 2008-03-07
> **boeing777 said:**
> sudo apt-get install compiz compiz-gnome compiz-plugins compiz-core csm

when I do that I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz has no installation candidate

---

### Post by boeing777 on 2008-03-07
System --> Administration --> Software Sources

Under "Ubuntu Software"  tab check all the checkboxes

Under "update" tab, check all the checkboxes

enable compiz and see what happens







if does not work try:

sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0

---

### Post by DXM31 on 2008-03-07
> **boeing777 said:**
> System --> Administration --> Software Sources

Under "Ubuntu Software"  tab check all the checkboxes

Under "update" tab, check all the checkboxes

enable compiz and see what happens..

actually that did alot I have all the compiz stuff back in synaptic package manager

I couldn't enable compiz thru apperance.
When I try to mark all the compiz stuff I can only mark certain ones, I guess there is a
confict when doing all of them at the same time??

The other bad news is the update icon is back, I'm afraid to update.
What to do??
Update the try and install compiz
install compiz then update
just install compiz and never update?

---

### Post by boeing777 on 2008-03-07
i wouldn't bother updating it. i would install compiz and never update.  what happens when you try to enable in appearance?

---

### Post by DXM31 on 2008-03-07
It's back:guitar:
should I install the rest of the compiz stuff like compiz-dev..

---

### Post by boeing777 on 2008-03-07
i would just install compiz-dev, This package contains the headers and libraries needed to compile compiz plugins.

so compiz is working now??

---

### Post by DXM31 on 2008-03-07
Yes it is, thanks for the help.
There are 209 updates available, I wonder how high that number will get.
Updating is dangerous.
The funny thing to me is Kiba never stopped working and thought it had to have compiz???

---

