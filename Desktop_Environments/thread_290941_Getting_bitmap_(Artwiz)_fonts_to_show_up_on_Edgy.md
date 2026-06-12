---
title: "Getting bitmap (Artwiz) fonts to show up on Edgy"
date: 2006-11-01
forum: Desktop Environments
---

### Post by Canordis on 2006-11-01
I've installed the artwiz font package through apt-get, and then did what I'm used to do - ran sudo dpkg-reconfigure fontconfig - to get bitmap fonts working under X11. Fontconfig doesn't show me the option to enable bitmap fonts anymore, so I'm stuck on how to enable them. This is fontconfig's output:
```
brd@bedlam:/etc/fonts$ sudo dpkg-reconfigure fontconfig
Password:
Cleaning up font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
Regenerating fonts cache... done.

```

Artwiz fonts aren't showing up at all, in fact:
```
brd@bedlam:/etc/fonts$ fc-list | grep artwiz
brd@bedlam:/etc/fonts$ 

```

---

### Post by johnnymac on 2006-11-02
I'm having the same issue.  So can anyone help??

---

### Post by pspotts on 2006-11-08
Hi,

For some reason, many posts on this mistype the command. The command should read:

>sudo dpkg-reconfigure fontconfig-config

Note the extra -config at the end of the fontconfig command. That will bring up the screen enabling you to activate bitmap fonts. Then artwiz will show up...

Pete

---

