---
title: "Compiz Probs After Emerald Install"
date: 2012-04-04
forum: Desktop Environments
---

### Post by Kodeine on 2012-04-04
Salutations!

So, once again, I fell to the allure of the window decorator emerald. Where, just like the first time around, (I know I know) upon attempting to back out of emerald to the safety of compiz I'm faced with a problem.

Seemingly after several minutes or after opening Chrome any window that isn't maximised has it's borders removed (so there's no close, minimise and maximise etc buttons). I can get them breifly back if I reload compiz via fusion-icon. After a brief chat on IRC it appears compiz is crashing. Here's a pastebin log of me running compiz via terminal.

[http://pastebin.com/sK65v4Fi](http://pastebin.com/sK65v4Fi)

I forgot my two vows of 'Never bother using Windows applications via wine or a VM' and 'Thou shalt never not use compiz'.

***GTK-Window-Decorator log```
gtk-window-decorator

(gtk-window-decorator:11027): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Segmentation fault

```

---

### Post by Frogs Hair on 2012-04-04
If you are using 11.10 only the Emerald package provided with the PPA at the link will work properly . The official Emerald package was removed from the 11.10 repository. [http://askubuntu.com/questions/79923/how-to-install-emerald-theme-manager-and-dual-switch-between-emerald-themes-and](http://askubuntu.com/questions/79923/how-to-install-emerald-theme-manager-and-dual-switch-between-emerald-themes-and)

---

### Post by Kodeine on 2012-04-05
Okay I've managed to fix it. If your also getting a segmentation fault when running gtk-window-decorator then this may solve the issue.

It appears that the ~/.gconf/apps/compiz-1 and compizconfig-1 folders are the culprit of this problem. I deleted them both and logged in and out again. This will create the two folders again and stop the borders missing issue and you can now happily carry on as usual.

You may want to backup your apps folder to put back some settings. I wanted my launcher back the same way and so I...

copied the **'unityshell'** folder from the _~/.gconf/apps/compiz-1/plugins/_ directory as well as from the _~/compizconfig-1/profiles/Default/plugins_ directory. Then pasted the two **'unityshell'** folders back in their newly created compiz-1 and compizconfig-1 folders respectively and this gave me back my nice unity dock. I think custom keyboard shortcuts are also stored in the apps folder somewhere too.

Have funzies!

---

