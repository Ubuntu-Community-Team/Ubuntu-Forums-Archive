---
title: "lastest feisty upgrade messed up my desktop"
date: 2007-05-18
forum: Desktop Environments
---

### Post by rpseng on 2007-05-18
Dear All,

I have just installed a upgrade, something related to 'metacity' if I can remember...

The problem is, the icons of the main menus are all missing, my mouse and keyboard configurations are weird (for instance, mouse motion is very fast).

Anybody knows what is happening??

Thanks in advance.

---

### Post by zvacet on 2007-05-18
system>settings>mouse and system>settings>keyboard  to correct behaviour of these

For icons right click on panel>add to panel>scroll down and you will see Ubuntu icon.Put it on the panel.

---

### Post by rpseng on 2007-05-18
> **zvacet said:**
> system>settings>mouse and system>settings>keyboard  to correct behaviour of these

For icons right click on panel>add to panel>scroll down and you will see Ubuntu icon.Put it on the panel.

Dear zvacet,

Thank you for your reply.
I tried to correct the behavior with system->settings->mouse and it doesn't respond to the changes.

Regarding the icons, I still have the menus. What is missing are the icons of each item. System->preferences, System->Administration, etc. are all without icon.

I really don't know the source of the problem.
If I go to System->Preferences->Theme then I get a message:

"The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly."

Any ideas?

---

### Post by Ambimom on 2007-05-18
Why not go to synaptic and search for metacity:  reinstall or install the themes mentioned in your error message.  Perhaps the recent update did not go through properly.  It's worth a try.

---

### Post by rpseng on 2007-05-20
> **Ambimom said:**
> Why not go to synaptic and search for metacity:  reinstall or install the themes mentioned in your error message.  Perhaps the recent update did not go through properly.  It's worth a try.

Dear Ambimom,

I tried to reinstall everything related to metacity and gconf but had no luck.

Maybe I'll have to use a Windows technique: reinstall the OS :(

---

### Post by rpseng on 2007-05-20
I've just fixed the problem.

In order to fix it I started the system using the recovery mode then I removed gconf2 and consequently all its dependencies (154 packages). Finally, I installed again the ubuntu-desktop package (and all its dependencies +100 packages).

As a result my system is now working perfectly again. Unfortunately I could not discover exactly what was the problematic package...

---

### Post by loweb1 on 2007-06-02
I think I'm having a very similar problem. My title bars disappeared and the panels quit working after a recent update. If I use beryl or compiz everything comes back. Maybe I'll have to follow your example and reinstall everything. 

What is gconf2 though? And did you replace it with something different by installing the ubuntu-desktop package or does that include gconf2?

---

### Post by loweb1 on 2007-06-02
Used synaptic to reinstall all things related to metacity and that seems to have fixed the problem, glad I only had to reinstall 4 packages rather than 100+.

Thanks for posting about this though, it helped point me in the right direction.

---

