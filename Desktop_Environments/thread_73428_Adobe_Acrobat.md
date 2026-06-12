---
title: "Adobe Acrobat"
date: 2005-10-09
forum: Desktop Environments
---

### Post by iakudi on 2005-10-09
Hi, I have downloaded and installed adobe (I think), but how can I:

1) Link it to firefox
2) When opeining a pdf document online ensure the acrobat plugin opens it within firefox and not try to launch xpdf
3) Use acrobat as default to open prf documents I save to my desktop.

Sorry if I sound dumb, but I tried following the advice on the starter guide but it does not work

iakudi

---

### Post by aysiu on 2005-10-09
Forget about the file you downloaded.
Follow [these instructions to get extra repositories](http://www.psychocats.net/sources.html).
Then ```
sudo apt-get update
sudo apt-get install mozilla-acroread
``` Then, you're done. It's installed.

---

### Post by iakudi on 2005-10-09
Thank you...I'm trying it now, just anoither question. I am still using Hoary 5.04 but some of the updates are from Breezy 5.10, does it matter?

Also, how "stable" is Breezy ? I hear it is really good..upgrade 5.04 or install new copy

thanks

Iakudi

---

### Post by iakudi on 2005-10-09
[QUOTE=aysiu]Forget about the file you downloaded.
Follow [these instructions to get extra repositories](http://www.psychocats.net/sources.html).
Then ```
sudo apt-get update
sudo apt-get install mozilla-acroread
``` Then, you're done. It's installed.[/QUOTE]



I tried this, everything installed fine but when I start a new firefox page and click on a pdf document it still asks me if I want to use xpdf to view it. 

Am I being stupid or should firefox now open it?

---

### Post by aysiu on 2005-10-09
[QUOTE=iakudi]Thank you...I'm trying it now, just anoither question. I am still using Hoary 5.04 but some of the updates are from Breezy 5.10, does it matter?

Also, how "stable" is Breezy ? I hear it is really good..upgrade 5.04 or install new copy

thanks

Iakudi[/QUOTE] On the page I linked to, it says **if** you're using Breezy, do this. **If** you're using Hoary, do this. You don't follow both sets of instructions.

Upgrading to Breezy is an entirely different process from just installing a few packages.

---

### Post by aysiu on 2005-10-09
[QUOTE=iakudi]I tried this, everything installed fine but when I start a new firefox page and click on a pdf document it still asks me if I want to use xpdf to view it. 

Am I being stupid or should firefox now open it?[/QUOTE] Go to Edit > Preferences > Downloads. Click on PDF and then click Remove. Then, go to a page with a PDF on it and it should ask what program you want to use. Select acroread. [Here's a screenshot of what my preferences look like](http://i22.photobucket.com/albums/b337/psychocats/dadeb2f4.png)

---

### Post by iakudi on 2005-10-09
ok, so I managed to upgrade to Breezy 5.10 (it looks really good). I can now see that acrobat is installed and when I goto a site to view a pdf document it launches a new firefox window and the dialog box offers me "Reader.pdf" before xpdf.

When I click ok the boc disappears BUT nothing happens - no document....I checked the preferences and there is nothing there...

---

### Post by aysiu on 2005-10-09
That's odd.
Well, maybe we can work around it. You know how you get that dialogue box? Instead of selecting one of the options that are suggested to you, how about clicking "Browse" and finding /usr/bin/acroread?

---

### Post by iakudi on 2005-10-09
amazing...like a "Windows" (ouch !!) reboot it all seems to work flawlessley now...thanks

---

