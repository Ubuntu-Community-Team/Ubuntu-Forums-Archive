---
title: "CRITICAL error on apt-get..."
date: 2006-02-01
forum: Desktop Environments
---

### Post by CyberAngel on 2006-02-01
When i am apt-geting programs most of the times I get a message for something CRITICAL on my console.

```

.......
Setting up kdepim-wizards (3.5.1-0ubuntu0breezy1) ...

** (process:20290): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

Setting up knotes (3.5.1-0ubuntu0breezy1) ...

** (process:20295): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

Setting up konq-plugins (3.5.1-0ubuntu0breezy1) ...

Setting up kontact (3.5.1-0ubuntu0breezy1) ...

** (process:20303): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

Setting up korganizer (3.5.1-0ubuntu0breezy1) ...

** (process:20309): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
...

```

Anyway it doesn`t seems that I have a problem at last, but does anyone know what might be the problem?

---

### Post by fdoving on 2006-02-01
Hi.
Your problem is a known problem. You can read more about it at:
[https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems)


- Frode

---

### Post by CyberAngel on 2006-02-02
[QUOTE=fdoving]Hi.
Your problem is a known problem. You can read more about it at:
[https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems)


- Frode[/QUOTE]


Thanks for the info :) 

Sorry if I am wrong but it doesn`t seems to report a solution (only the problem) and as I can see in the "Known Problems with Kubuntu's KDE 3.5 final" section it does not exist such an error...

This is a KDE`s rc1 known problem.
I had never install an unstable KDE version....
I went directly to KDE 3.5.0 and now I have upgrade it to KDE 3.5.1

---

### Post by suziequzie on 2006-07-04
I have replaced this line (no quotes)

"Type=Application"
with this line 

"MimeType=application/x-desktop"

and that appeared to fix the problem. Lemme know if it helps any.

 :D

---

### Post by CyberAngel on 2006-07-04
When I had that problem I was in breezy :)

Now in dapper I have no problem.

Thanks for the reply anyway ;)

---

