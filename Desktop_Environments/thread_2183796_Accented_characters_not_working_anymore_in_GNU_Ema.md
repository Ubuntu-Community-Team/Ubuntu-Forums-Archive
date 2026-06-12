---
title: "Accented characters not working anymore in GNU Emacs"
date: 2013-10-26
forum: Desktop Environments
---

### Post by buisteric on 2013-10-26
Hi,

I am writing French text documents using GNU Emacs and just after upgrade to Ubuntu 13.10, I am getting problems entering characters such as é, è, etc. No matter what keyboard layout I choose (Canadian French or US International), some characters require two keys to be pressed, e.g., ' and e for the é. Emacs seems to now ignore the first key and just displays the non-accented character. I can enter accents elsewhere, such as the terminal or a Chrome window. All other text editors under Ubuntu I tried just suck: no support for GNUPG, too small characters that cannot be enlarged, inconvenient search and replace not working without clicking multiple times at multiple places with the mouse, lack of UTF-8 support, etc.

Any search on Google now lead to irrelevant results. Searching about GNU Emacs gives a first hit about Octave and other hits are just helpless. It seems that Google just doesn't do the job anymore. Is there another search engine that replaced Google I am not aware of?

Thanks in advance for any help.

---

### Post by buisteric on 2013-10-26
Hi,

I partially fixed the issue by adding the following to ~/.emacs:

(require  'iso-transl)

With this, most characters work, except ç. I still cannot find ANY way to produce this ç with Emacs under Ubuntu 13.04, except copy/pasting it from another window or define a non-standard keyboard shortcut that would insert it by character code.

---

### Post by buisteric on 2013-10-26
Hi again,
Just found another work around: start Emacs with XMODIFIERS='' emacs. All dead keys work even without the need for the iso-transl extension. I don't like this, because that means no way to start Emacs from the Unity Dash. I tried searching for an hour without results: no other way out, no other text editor supporting GnuPG integration (tried Geany, GnuPG not working) except Vim which is virtually unusable for me (too counter-intuitive workflow).

---

### Post by twinoatl on 2013-11-14
Please add info to
[https://bugs.launchpad.net/emacs-snapshot/+bug/1251176](https://bugs.launchpad.net/emacs-snapshot/+bug/1251176)
and
[http://debbugs.gnu.org/cgi/bugreport.cgi?bug=15891](http://debbugs.gnu.org/cgi/bugreport.cgi?bug=15891)

Thank you for your workarounds.

---

