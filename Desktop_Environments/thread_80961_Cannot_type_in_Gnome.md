---
title: "Cannot type in Gnome"
date: 2005-10-23
forum: Desktop Environments
---

### Post by kupokomapa on 2005-10-23
Hello,

I just upgrade my hoary to breezy and at first all was ok as I caould reboot and use everything as before. I noticed at some point though that I cannot type in gaim, terminals, alsmost everything that is based on GTK2. I could still type in firefox and the rest which differs from the problems that other users reported on the forum before me. I am really out of luck because I cannot even login to Gnome after the latest restart. The keyboard is working as I can press CTRL+ALT+F1 to switch to the console and I can login there and do everything I want but I do not know where te problem is and where to look for (log files, etc).

I am using a Compaq nx7000 with both an USB keyboard and the built-in one which both do not work. Please, if somebody has experienced that and knows a way to solve it, please post here :)

Thanks in advance!

---

### Post by LorenzoD on 2005-10-23
Do you have SCIM installed by any chance? If you do sudo $EDITOR /etc/gtk-2.0/gtk.immodules and comment out the section relating to SCIM.

Edit: Your $EDITOR variable may or may not be defined. Replace that with your text editor of choice (vim, emacs, nano, gedit or whatever).

---

### Post by kupokomapa on 2005-10-23
[QUOTE=LorenzoD]Do you have SCIM installed by any chance? If you do sudo $EDITOR /etc/gtk-2.0/gtk.immodules and comment out the section relating to SCIM.

Edit: Your $EDITOR may or may not be defined. Replace that with your text editor of choice (vim, emacs, nano, gedit or whatever).[/QUOTE]

Commented it out and restarted X but did not solve the problem. Should I completely uninstall it and how :)

Thanks

---

### Post by LorenzoD on 2005-10-23
It seems the current SCIM packages are buggy. I removed mine as I was having the same problems as you. From what I hear we may be getting new SCIM packages in Dapper. If you need to be able to input Japanese, you can try UIM instead, which works okay for me.

To remove SCIM, open synaptic, search for scim and select remove (or does it say uninstall?). I'd do that and see what happens.

---

### Post by kupokomapa on 2005-10-23
[QUOTE=LorenzoD]It seems the current SCIM packages are buggy. I removed mine as I was having the same problems as you. From what I hear we may be getting new SCIM packages in Dapper. If you need to be able to input Japanese, you can try UIM instead, which works okay for me.

To remove SCIM, open synaptic, search for scim and select remove (or does it say uninstall?). I'd do that and see what happens.[/QUOTE]


Well, I could not login to X at all so synaptic was not a choice so I just did apt-get remove scim and it took care of it. I restarted X again but no luck :( I am rebooting the whole OS just to make sure it does not solve the problem. So you had the same problem as me and this solved it. Again it seemed to be working in the beginning as I could login to X but not anymore and I did not change anything apart from going to settings and changing the default language as it said that now KDE and GNOME us different translations.

---

### Post by kupokomapa on 2005-10-23
somebody?

---

### Post by LorenzoD on 2005-10-23
One more thing: did you have scim-gtk2-immodule installed? And was it removed by the apt-get uninstall you did on scim? If not, do remove that one as well.

---

### Post by kupokomapa on 2005-10-23
[QUOTE=LorenzoD]One more thing: did you have scim-gtk2-immodule installed? And was it removed by the apt-get uninstall you did on scim? If not, do remove that one as well.[/QUOTE]

Yes, it was removed and also regenerated the config file that you mentioned in the first post without the SCIM includes. What else could be the problem. It just  does not want to input where there are input fields like the username and password on the GDM. If it goes to screensaver, pressing a key gets back in the login prompt so it records the keystrokes but that's about it.

Kupo

---

### Post by LorenzoD on 2005-10-23
Anything in ~/.xsession-errors? Log files?

---

### Post by kupokomapa on 2005-10-23
[QUOTE=LorenzoD]Anything in ~/.xsession-errors? Log files?[/QUOTE]

No, nothing!

---

### Post by kupokomapa on 2005-10-23
Well, I fix it. Actually I do not know what was the problem but under the console I did apt-get dist-upgrade and all is ok now. Maybe I did not do a full update to Breezy and something was missing.

I hope this helps somebody else.

Kupo

---

### Post by LorenzoD on 2005-10-23
Well good that you did get it resolved. Sorry I couldn't help you. But since I had experienced exactly the same problem and mine was related to SCIM, I was certain that it was the culprit in your case as well.

If you feel adventurous, you could always try to re-install SCIM and see what happens. :smile:

---

