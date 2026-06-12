---
title: "Tint2 Configuration"
date: 2009-02-03
forum: Desktop Environments
---

### Post by andras artois on 2009-02-03
Is possible to configured Tint to look like the picture I've included?
Also can I setup a menu button (like in the picture) to go to the Openbox menu?
I know Tint2 dosn't have a tray and was wondering whether you could do this by using trayer?

Thanks.

---

### Post by Dawei87 on 2009-05-19
im not positive, but i think that looks like lxpanel. which is in the repos, if not im not sure how they did that. maybe custom background images?

---

### Post by mcduck on 2009-05-20
> **andras artois said:**
> Is possible to configured Tint to look like the picture I've included?
Also can I setup a menu button (like in the picture) to go to the Openbox menu?
I know Tint2 dosn't have a tray and was wondering whether you could do this by using trayer?

Thanks.

Not possible. Tint2 doesn't support application launchers, menus, or panel applets.

You'll have to try some other panel like lxpanel or pypanel instead.

---

### Post by Killeroid on 2009-05-20
> **mcduck said:**
> Not possible. Tint2 doesn't support application launchers, menus, or panel applets.

You'll have to try some other panel like lxpanel or pypanel instead.

Actually, tint2 does have a system tray. Check my signature for the link the tint2 ppa which contains svn builds of tint2. The current titn2 package in the ubuntu repos is of an old version(which doesn thave a system tray) but the packages in my repo are new bleeding edge stable stuff

---

### Post by mcduck on 2009-05-20
> **Killeroid said:**
> Actually, tint2 does have a system tray. Check my signature for the link the tint2 ppa which contains svn builds of tint2. The current titn2 package in the ubuntu repos is of an old version(which doesn thave a system tray) but the packages in my repo are new bleeding edge stable stuff

Yes, I know it has notification area. I've been using packages from your repository for quite a while now (thanks for that, BTW :D). I didn't say it doesn't have one. I said it doesn't have support for *menus, launchers or panel applets*.

---

### Post by fiddler616 on 2010-01-06
> **mcduck said:**
> Yes, I know it has notification area. I've been using packages from your repository for quite a while now (thanks for that, BTW :D). I didn't say it doesn't have one. I said it doesn't have support for *menus, launchers or panel applets*.

Maybe I'm joining the party a bit late, but I'm sitting here with my Crunchbang 9.04 laptop, happily enjoying nm-applet, the volume controller, etc. with tint2. I can post my .tint2rc if that's deemed helpful, but it might just be that applet support was added between May and now.

---

### Post by mcduck on 2010-01-06
> **fiddler616 said:**
> Maybe I'm joining the party a bit late, but I'm sitting here with my Crunchbang 9.04 laptop, happily enjoying nm-applet, the volume controller, etc. with tint2. I can post my .tint2rc if that's deemed helpful, but it might just be that applet support was added between May and now.

All those are actually notification icons (even though nm-applet's name does suggest otherwise), none of them is a panel applet. Even the latest version of Tint2 doesn't have support for any type of applets (apart from the built-in battery & clock features).

---

### Post by Jose Catre-Vandis on 2010-01-06
I wonder if much of it is possible (certainly the three on the right) by running multiple instances of tint2 with different configuration files? The two on the left would have to be a kludge of some kind to be functional in anyway, but you could use xfce-panel in some way.

No, I do not believe you can't have icons in the Openbox Menu, or couldn't the last time I looked.

---

