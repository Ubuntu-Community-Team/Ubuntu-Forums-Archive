---
title: "Intaller Crash"
date: 2012-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MartianTek3 on 2012-06-24
Recently, I had Windows 7, I got sick of all the BSODS 
Then decided to clean my new Dell Inspiron N5110 of Windows FOREVER 

I booted off the latest Kubuntu 12.04 LTS (AMD64) 

I used Kubuntu before,went through the setup: Language, Prepare, Disk Setup, Timezone, then User Info

I filled the User Info page and once i clicked 'Continue' 

Installer Crash: 

[COLOR=Red]Traceback (most recent call last):
  [/COLOR][COLOR=Red]File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 957, in on_next_clicked
    self.dbfilter.ok_handler()
  File "/usr/lib/ubiquity/plugins/ubi-usersetup.py", line 806, in ok_handler
    self.ui.hostname_error(make_error_string(self.controller, errors))
AttributeError: 'Page' object has no attribute 'controller'
[/COLOR]
I got this Exact same Error message every single time i tried installing Kubuntu on my System 

I tried Using Kubuntu Boot CD 32 and 64 bit

then booted off a USB, same thing 

As a last resort i will try to boot Ubuntu 12.04, see what happens 

Sincerely, 
MartianTek3

---

### Post by ajgreeny on 2012-06-24
I suggest you try booting to the desktop of the live CD system, then run ```
sudo apt-get remove ubiquity-slideshow-kubuntu
``` the try the installation again by double clicking on the Install icon.

It seems to be a bug causing crashes of the ubiquity slideshow, which then takes the rest of ubiquity with it; no ubiquity running means no installation.

Worth a try, but if that is no good try the alternate installation CD, which uses a text installer and not a live system; still easy to do!

---

### Post by MartianTek3 on 2012-06-25
the Command didn't work 

But Thank God the Alternate Live CD was a success 

Thank you for your help ajgreeny 

Currently, Kubuntu 12.04 is running like a beast 

[SOLVED] 

Martian Out

---

