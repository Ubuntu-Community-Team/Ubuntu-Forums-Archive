---
title: "Missing Key..."
date: 2005-04-19
forum: Desktop Environments
---

### Post by Xeon3D on 2005-04-19
Hi.

I'm a portuguese Kubuntu owner and I'm having some problems with my Keyboard Layout.

Every key works perfectly (accents included - example: á é í etc...ã ) but one key.

The single « (the one you use to start html tags with) will simply not function.. this inside KDE.

If I CTRL + ALT + F1-F6 and log in, the key works as expected (1).

So how can I fix it?

(1) In the bash prompt (CTRL+ALT+F1-F6) if I type 3 or 4 accented letters like "áááá" the next key I press is going to put another "á" instead of what they key would normally do.

Example:
*Writes 4 times á*

x@coffin:~$áááá

*Presses the  "P" key*

x@coffin:~$áááá**á**

*Presses the "P" key again*

x@coffin:~$áááá**áp**.

If anyone knows the cure for this please advice. :P
Thanks in advance.
Marcos.

---

### Post by Ironi on 2005-04-20
I don't know whether or not it will work, but you can try this:

**sudo apt-get install kde-i18n-pt kde-i18n-ptbr**

**kcmshell language**
(set the language)

**kcmshell keyboard**
(comes up blank here...)
 
 
Hope that helps.

---

