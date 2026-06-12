---
title: "Unable to create more than 1 workspace"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by bigpru on 2008-01-13
I am running compiz (I have enabled Advanced Desktop Effects Settings) and I lost the ability to create more than one workspace after I opened "Preferences > GL Desktop" and accepted changes.

I have tried right clicking the ws thumbnail and changing the columns to 4 and the rows to 1 and it still just displays one ws and I am also unable to switch desktops with keyboard shortcuts..

I am running 7.10 and am a newbie. Thanks in advance for the help.

---

### Post by overdrank on 2008-01-13
> **bigpru said:**
> I am running compiz (I have enabled Advanced Desktop Effects Settings) and I lost the ability to create more than one workspace after I opened "Preferences > GL Desktop" and accepted changes.

I have tried right clicking the ws thumbnail and changing the columns to 4 and the rows to 1 and it still just displays one ws and I am also unable to switch desktops with keyboard shortcuts..

I am running 7.10 and am a newbie. Thanks in advance for the help.

Hi and welcome,  you can try this command to install the manager
```
sudo apt-get install compizconfig-settings-manager
```
Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also make sure the rotate cube box is checked.

---

### Post by bigpru on 2008-01-13
I already had that installed and I have tried (and just now retried) that with no luck.

---

### Post by overdrank on 2008-01-13
> **bigpru said:**
> I already had that installed and I have tried (and just now retried) that with no luck.

Ok have you tried switching the desktops on the panel to one and one row?

---

### Post by bigpru on 2008-01-13
For some reason I was *just* able to make that change. I don't know why but, I ran:

```
sudo apt-get install compizconfig-settings-manager
```

then I retried changing the "workspace switcher" to Rows:1 Columns: 4 and it worked!

---

