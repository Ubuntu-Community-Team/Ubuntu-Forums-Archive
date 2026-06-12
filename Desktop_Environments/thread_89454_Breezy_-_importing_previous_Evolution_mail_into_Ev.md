---
title: "Breezy - importing previous Evolution mail into Evolution 2.4"
date: 2005-11-12
forum: Desktop Environments
---

### Post by jameswilhelm on 2005-11-12
Hi,

I did a search on the forums, but could not find an answer.

How do I import my evolution folder from the previous version of Evolution (in Hoary), to version 2.4 in Breezy? The previous version would detect the old Evolution folder and simply import it. Version 2.4 does not do that. Copying the old "evolution/"  folder to ".evolution/" has no effect, it simply ignores it and displays empty mail folders.

Unsubscribe/subscribe is not the solution. The import function does not give an option for pointing Evolution at old Evolution folders - it just searches for other 'older' email programs and tries to import email from them.

The Evolution user manual is no help in this case.

At the moment I'm stuck and cannot get at my email :-). I'm probably missing something obvious, but have run out of ideas.

Any help appreciated.

James

---

### Post by dcstar on 2005-11-12
[QUOTE=jameswilhelm]Hi,

I did a search on the forums, but could not find an answer.

How do I import my evolution folder from the previous version of Evolution (in Hoary), to version 2.4 in Breezy? The previous version would detect the old Evolution folder and simply import it. Version 2.4 does not do that. Copying the old "evolution/"  folder to ".evolution/" has no effect, it simply ignores it and displays empty mail folders.

Unsubscribe/subscribe is not the solution. The import function does not give an option for pointing Evolution at old Evolution folders - it just searches for other 'older' email programs and tries to import email from them.

The Evolution user manual is no help in this case.

At the moment I'm stuck and cannot get at my email :-). I'm probably missing something obvious, but have run out of ideas.

Any help appreciated.

James[/QUOTE]
Your old e-mail should have been in a hidden ".evolution" folder in your Home directory.

If you have changed user names in the upgrade/reinstalled onto a new file system, simply copy that whole directory to your new Home directory.

Then start Evolution and you should have the same data as the old installation.

---

### Post by jameswilhelm on 2005-11-13
Hi, David.

Thanks for the reply. I tried that - no luck. I also discovered an evolution directory created by Evolution in ~/.gconf. Also tried ~/evolution/

I uninstalled Evolution (the complete uninstall) and deleted ~/evolution, ~/.evolution and ~/.gconf/evolution. Then reinstalled Evolution, copied all my files to ~/.evolution and then ran Evolution - no luck. Tried the same with the ~/.gconf/evolution directory and with an ~/evolution directory.

This is getting rather silly. My Evolution upgrade when switching from Redhat 9 to Hoary was painless - Evolution did all the work. This time it seems that either something went wrong, or it is made very difficult for some reason. Not the way to sell Desktop Linux to the masses!

Any other ideas appreciated.

Regards.

James

---

