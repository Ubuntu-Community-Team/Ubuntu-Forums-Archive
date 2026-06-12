---
title: "Firefox"
date: 2009-05-11
forum: General Help
---

### Post by akas on 2009-05-11
Hi, 
I'm pretty new to Ubuntu/linux and doesn't have much experience.

One thing i can't figure out is how to set a new homepage in firefox/ubuntu.
The problem is not how to, but why Firefox doesn't save my setting.

If I set a new homepage, and then restart Firefox, my settings are lost. And my homepage have reset to standard.
Also if I run firefox in superuser mode "$ sudo firefox", my old setting is back. 

Why wont firefox save my settings?
And how can I fix it?
Thanks.

Sry for my bad English.

---

### Post by Fingers &amp; Thumbs on 2009-05-11
Hello akas,

i have not had this problem myself, i have never needed superuser priveledges to set my homepage, but everyones setup is somehow different.

It is possible that you may have better luck using gksudo instead of sudo in this case, the general rule is gksudo for graphical (GUI) applications, sudo for console/terminal apps.

I hope this helps.

P.S. No need to apologise for your english, it is much better than my atempts at a second language.

---

### Post by Paqman on 2009-05-11
> **Fingers & Thumbs said:**
> 
It is possible that you may have better luck using gksudo instead of sudo in this case, the general rule is gksudo for graphical (GUI) applications, sudo for console/terminal apps.


No, that's not a good idea. NEVER run your browser using sudo/gksudo. Doing so could allow an attacker to compromise your system.

Akas, you might want to throw out your old Firefox settings and start fresh. Go to Places > Home and hit Ctrl-H, then go delete the folder .mozilla. Then restart Firefox and go to the page you want as your home page, then Edit > Preferences > Use Current Page.

---

### Post by akas on 2009-05-11
Thanks Paqman, it worked.
Do you have a explanation?
Or was it just a weird system setting in firefox?
Thanks again.
__

---

### Post by gfg on 2009-05-11
Just wanted to contribute a tip I recently found out. You can set a new homepage fast and easy by dragging the location bar icon to the homepage button. Not that relevant, but hey someone might find it useful.

---

### Post by Paqman on 2009-05-11
> **akas said:**
> Thanks Paqman, it worked.
Do you have a explanation?
Or was it just a weird system setting in firefox?
Thanks again.
__

The folder .mozilla contains all your personal settings for Firefox. That includes stuff like your homepage and bookmarks. Clearly something had gone wonky in there, so it's often easiest to delete it completely and start fresh.

---

