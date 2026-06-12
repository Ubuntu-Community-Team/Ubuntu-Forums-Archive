---
title: "Grayed out Shares-Admin?"
date: 2006-04-15
forum: Desktop Environments
---

### Post by jreyst on 2006-04-15
I originally posted this in the Absolute Beginners section but got no response at all after several days so I'm reposting here. Hope I'm not breaking any cross-posting rules.

For the last week or two whenever I open the shares-admin gui it just stays gray and no buttons or shares or anything ever become 'click-able'. I was thinking I might just re-install it but apt can't find it. Any thoughts? On a separate but maybe related note, all apps that I sudo open don't have the same theme applied to them that I have running otherwise. Things like gconf-editor, shares-admin, basically any gui tool I run via sudo. I could guess thats because they are running as a different user (root) than my own login, but I seem to recall my theme being applied to those things back when I first started running ubuntu. This is in Breezy by the way in case it matters.
](*,)

---

### Post by Ramses de Norre on 2006-04-15
To apply your theme to root: ```
sudo ln -s /home/<insert your username here>/.themes /root/.themes && sudo ln -s /home/<insert your username here>/.icons /root/.icons && sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

What are the permissions on /etc/samba/smb.conf ?

---

### Post by jreyst on 2006-04-15
Thanks for the quick response :)

[QUOTE=Ramses de Norre]What are the permissions on /etc/samba/smb.conf ?[/QUOTE]

-rw-r--r--  1 root root 7746 2006-04-12 00:33 /etc/samba/smb.conf

---

### Post by Ramses de Norre on 2006-04-15
Run ```
 gksudo shares-admin
``` in terminal and check for any error messages.

---

### Post by jreyst on 2006-04-15
[QUOTE=Ramses de Norre]To apply your theme to root: ```
sudo ln -s /home/<insert your username here>/.themes /root/.themes && sudo ln -s /home/<insert your username here>/.icons /root/.icons && sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```[/QUOTE]

By the way, the above seems to have resolved my issue. Thanks again. Now my root applications look as nice as my normal ones. Not sure how that got whacked in the first place but I thought it used to be that way. Anyway, its working now. You get a :KS

---

### Post by jreyst on 2006-04-15
[QUOTE=Ramses de Norre]Run ```
 gksudo shares-admin
``` in terminal and check for any error messages.[/QUOTE]

john@Colossus:~$ gksudo shares-admin
(shares-admin:10493): GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

