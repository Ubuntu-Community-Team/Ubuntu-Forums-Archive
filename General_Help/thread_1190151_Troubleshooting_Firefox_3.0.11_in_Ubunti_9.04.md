---
title: "Troubleshooting Firefox 3.0.11 in Ubunti 9.04"
date: 2009-06-17
forum: General Help
---

### Post by kelvinator on 2009-06-17
I am running firefox on a desktop and laptop with Ubuntu 9.04.

The browser on the desktop handles flash sites correctly. The browser on the laptop does not. The laptop was a fresh install, the desktop has been upgraded since version 7.04.

What sort of things should I check in Mozilla Firefox when it does not work as expected?

---

### Post by Diegstroyer on 2009-06-17
For upgrade to a new version you need to pass for all versions before the version do you wish, with all updates of any version.

If you launch firefox in console, what messages do you have?

---

### Post by lswb on 2009-06-17
Check which flash version (if any) the laptop is running. From Firefox menu, Tools/Addons/Plugins and look for Shockwave Flash for the Adobe version, or you may have the open source gnash alternative instead. 

The latest adobe version can be installed from synaptic. Enable the universe, multiverse, and restricted repositories, then search for flash, look for a package named "flashplugun-nonfree" or "adobe-flashplugin"

---

### Post by lovinglinux on 2009-06-17
Its probably not a Firefox problem, but a flash problem. 

Try to remove alternative versions like gnash and swfdec and install the adobe flash plugin.

Open "Applications >> Acessories >> Terminal", paste the comand below and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree
```

---

### Post by beesblaas on 2009-07-13
Thank you Lovinglinux, problem fixed !!!!!!!!

In my case I had Ubuntu 9.04 with Firefox 3.0.11,
and Firefox > Tools > Add-ons > plugins,  indicated Shockwave 9.0 r999

Some webpages would just miss content, miss pictures (photos) and menu stuff etc.

I was lead in the wrong direction by thinking I can solve it by installing Firefox 3.5 (Shiretoko). It did not help.
I also deleted the  <username>/.mozilla.firefox directory, but that did not fix it either.

I opened a terminal window, pasted in the command exactly as you gave it, and it fixed my problem !!!!!!!!!! (after about a minute of installation stuff, and I just typed "Y" every time I was prompted.) 
Note gnash was not present, so not removed, but it  did remove swfdec-mozilla )
:p


Now Firefox indicates Shockwave Flash 10.0 r22, and its fixed !

---

### Post by lovinglinux on 2009-07-13
> **beesblaas said:**
> Thank you Lovinglinux, problem fixed !!!!!!!!

In my case I had Ubuntu 9.04 with Firefox 3.0.11,
and Firefox > Tools > Add-ons > plugins,  indicated Shockwave 9.0 r999

Some webpages would just miss content, miss pictures (photos) and menu stuff etc.

I was lead in the wrong direction by thinking I can solve it by installing Firefox 3.5 (Shiretoko). It did not help.
I also deleted the  <username>/.mozilla.firefox directory, but that did not fix it either.

I opened a terminal window, pasted in the command exactly as you gave it, and it fixed my problem !!!!!!!!!! (after about a minute of installation stuff, and I just typed "Y" every time I was prompted.) 
Note gnash was not present, so not removed, but it  did remove swfdec-mozilla )
:p


Now Firefox indicates Shockwave Flash 10.0 r22, and its fixed !

You are welcome. For future reference and other tips, visit [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

