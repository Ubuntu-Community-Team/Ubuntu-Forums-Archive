---
title: "Unable to download Firefox Add-Ons on Ubuntu 10.0.4 Netbook Edition"
date: 2010-07-09
forum: Desktop Environments
---

### Post by leekb on 2010-07-09
Hello

I have just done a fresh install of Ubuntu 10.0.4 Netbook Edition on my Asus Eee PC 1000H, which was originally running Windows XP. Right after the installation I used the Update Manager to download/install updates. It works fine so far and I think I am beginning to like it.

I just could not get my head around one issue with the Firefox 3.6.6. For some strange reasons I just could not download and install Firefox add-ons or themes. I would click on the button "Add to Firefox". The download window with the progress bar would appear. The progress bar would get stuck at 0% with the message "waiting". After 30 secs or so, this error message would appear:

Firefox could not install the file at 

[https://addons.mozilla.org/en-us/firefox/downloads/file/92118/tab_mix_plus-0.3.8.4-fx.xpi?src=api&confirmed=1](https://addons.mozilla.org/en-us/firefox/downloads/file/92118/tab_mix_plus-0.3.8.4-fx.xpi?src=api&confirmed=1)

because: Download error
-228


Has anyone come across this before?

Thanks in advance

KB

---

### Post by lovinglinux on 2010-07-09
Instead of clicking the "Add to Firefox" button, right-click and select "Save link As". You will download a xpi file. Then click "File >> Open File" and select the xpi file you just downloaded. It will install as usual.

If you still has problems, try to download the extension xpi file with another browser to see if the problem persists.

---

### Post by leekb on 2010-07-11
Found the answer after several hours of searching. I found bugs opened against this issue, which seems to be fairly common.

_**Cause:**_ Firefox was sending IPv6 packets during add-ons download, disrupting normal operation. Or something to that effect.

_**Resolution:**_ Access ***about:config*** in Firefox, find the attribute **network.dns.disableIPv6** and set it to **true**. Problem solved.

---

### Post by apple2user on 2011-02-23
Really glad I found this! Had the exact same problem.

Just to clarify. about:config is accessed by typing it in the location bar. Took me a while to realize this (after searching for more help...)

---

