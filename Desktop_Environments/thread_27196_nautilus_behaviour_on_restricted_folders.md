---
title: "nautilus behaviour on restricted folders"
date: 2005-04-15
forum: Desktop Environments
---

### Post by Kymon on 2005-04-15
apparently if nautilus displays a file or folder with a little square with a white cross on a red background, it means that access to such a file or folder is forbidden.
is it a desired behaviour that nautilus "hides" such a folder if you right-click on it, and even quits itself when left-clicking twice on such a folder?
If that behaviour is intended, it would be nice if at least a message is given to the user, as it's quite confusing if you click on something in nautilus, and suddenly nautlius vanishes.

---

### Post by andvaranaut on 2005-04-15
Hi kymon

The problem is that by default Nautilus closes the window when you double click on a folder. If the folder you have just double clicked on is forbidden, Nautilus is not able to open it, and the net result is that you lose the window.

This Nautilus change was introduced at the last minute, and therefore still has some minor problems.

The solution is changing the Nautilus behaviour to something saner. You have two options:

- Leave the parent windows open when double clicking ('spatial' behaviour): Go to Applications > System Tols > Configuration Editor. Navigate to apps_nautilus_preferences. Check the no_ubuntu_spatial option in the list on the right. Close the configuration editor. Now, when you double click on a folder, the old window remains open.
- Make each folder open on the same window ('browser' behaviour): In any Nautilus window, click Edit > Preferences. In the Behaviour tab, check 'Always open in browser window'. Alternatively, you can open the Configuration Editor as before and check 'always_use_browser'. Now you will get 'Windows-like' behaviour.

I personally prefer the first option (takes some getting used to, but in the end it makes you very productive!), but wouldn't mind using the second. I think that the default mode has been a big mistake, though.

Hope this helps.

---

### Post by Kymon on 2005-04-15
hi andvaranaut,

thanks a lot for your explanation, the described behaviour does make perfect sense in combination with the spatial metaphor.

---

### Post by duffman25 on 2005-06-18
[QUOTE=andvaranaut]Hi kymon

The problem is that by default Nautilus closes the window when you double click on a folder. If the folder you have just double clicked on is forbidden, Nautilus is not able to open it, and the net result is that you lose the window.

This Nautilus change was introduced at the last minute, and therefore still has some minor problems.

The solution is changing the Nautilus behaviour to something saner. You have two options:

- Leave the parent windows open when double clicking ('spatial' behaviour): Go to Applications > System Tols > Configuration Editor. Navigate to apps_nautilus_preferences. Check the no_ubuntu_spatial option in the list on the right. Close the configuration editor. Now, when you double click on a folder, the old window remains open.
- Make each folder open on the same window ('browser' behaviour): In any Nautilus window, click Edit > Preferences. In the Behaviour tab, check 'Always open in browser window'. Alternatively, you can open the Configuration Editor as before and check 'always_use_browser'. Now you will get 'Windows-like' behaviour.

I personally prefer the first option (takes some getting used to, but in the end it makes you very productive!), but wouldn't mind using the second. I think that the default mode has been a big mistake, though.

Hope this helps.[/QUOTE]


Hi, I'm using the browser behaviour & when I try to open a folder which I can't read instead of telling me I don't have enought privileges to open it it closes. Is this a feature or a bug?

Thanxs

---

