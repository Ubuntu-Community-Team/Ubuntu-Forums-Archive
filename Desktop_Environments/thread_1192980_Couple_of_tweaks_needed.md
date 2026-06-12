---
title: "Couple of tweaks needed"
date: 2009-06-20
forum: Desktop Environments
---

### Post by anycon on 2009-06-20
When I go Administration -> Login Window the panel that pops up exceeds the bottom margin of my screen. I can't resize it upwards. Is there a fix?

Also, and this is really trivial: is there a tweak that will automatically 'select all' when I click to the address or search bars in Firefox and Opera?

---

### Post by raymondh on 2009-06-20
> **anycon said:**
> When I go Administration -> Login Window the panel that pops up exceeds the bottom margin of my screen. I can't resize it upwards. Is there a fix?


I hope I understand your issue.

Press ALT + left Mouse and drag up until you get the corner to resize

---

### Post by anycon on 2009-06-20
Works like a charm. Nothing on my second question? It would just make browsing quicker.

---

### Post by raymondh on 2009-06-20
> **anycon said:**
> Works like a charm. Nothing on my second question? It would just make browsing quicker.


Hi anycon,

let's try (if I understood your 2nd request as well)

-Open firefox
-Type  **about:config**  in the address bar
-Browse to the value  **browser.urlbar.clickselectsall**
-Right click and select **TOGGLE** to change value to *TRUE*
-Close and see if it works.  If not, re-do and change value back to FALSE

Usually, ALT + D will highlight the address or search bar for me.

Hope this helps.

---

### Post by anycon on 2009-06-22
Thanks very much. When I start up on the multiboot screen I get what seem like two versions of Ubuntu, one identified by a code ending in 13 and one by a code ending in 11. Is that normal?

---

### Post by xtjacob on 2009-06-22
Yes that is normal. The one ending in 13 is Kernel version 2.6.28.13 which is the latest. The one ending in 11 is kernel 2.6.28.11 which comes with Ubuntu 9.04.

---

### Post by raymondh on 2009-06-22
> **anycon said:**
> Thanks very much. When I start up on the multiboot screen I get what seem like two versions of Ubuntu, one identified by a code ending in 13 and one by a code ending in 11. Is that normal?

You may want to download/install (either thru synaptic or terminal) startup manager.  It is a GUI application that allows you options to choose which kernel or OS to boot, how many seconds, etc.

---

### Post by anycon on 2009-06-22
Thanks again. What's the stablest way to view Flash video on the web? I'm having real trouble with something so simple as YouTube. In Firefox it's laggy and in Opera it doesn't work at all.

---

### Post by raymondh on 2009-06-22
> **anycon said:**
> Thanks again. What's the stablest way to view Flash video on the web? I'm having real trouble with something so simple as YouTube. In Firefox it's laggy and in Opera it doesn't work at all.


You may want to try ubuntu-restricted-extras.  

Or, you may want to try the 'official' version from adobe.

You may use terminal, synaptic or add/remove (but only one at a time).

---

