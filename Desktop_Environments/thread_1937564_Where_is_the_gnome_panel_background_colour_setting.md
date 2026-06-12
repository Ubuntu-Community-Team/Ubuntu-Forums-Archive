---
title: "Where is the gnome panel background colour setting kept?"
date: 2012-03-08
forum: Desktop Environments
---

### Post by crf on 2012-03-08
In the panel, the colour can be changed
Alt-rightclick on the panel, choose properties, background, edit the colour.

Where is this setting stored?

---

### Post by 73ckn797 on 2012-03-08
> **crf said:**
> In the panel, the colour can be changed
Alt-rightclick on the panel, choose properties, background, edit the colour.

Where is this setting stored?

I find the info via ```
gconf-editor
``` under desktop/gnome/background. You may have to install "gconf-editor" from Synaptic.

---

### Post by crf on 2012-03-08
Thanks,

Is that setting not for the Desktop, rather than the panel?

---

### Post by crf on 2012-03-08
I think I found it. It is stored as something called a *gsettings*. The gui program to use to view/edit them is dconf-editor (rather than gconf-editor). The command line program gsettings can be used to view or edit them.

If you use the dconf-editor, the setting will be shown as:

```
org:gnome:desktop:gnomepanel:layout:toplevels:top-panel:background
```

[dconf](https://live.gnome.org/dconf)

---

### Post by 73ckn797 on 2012-03-09
> **crf said:**
> I think I found it. It is stored as something called a *gsettings*. The gui program to use to view/edit them is dconf-editor (rather than gconf-editor). The command line program gsettings can be used to view or edit them.

If you use the dconf-editor, the setting will be shown as:

```
org:gnome:desktop:gnomepanel:layout:toplevels:top-panel:background
```[dconf]("https://live.gnome.org/dconf")
You did not state which version of Ubuntu you were using so I assumed it was 10.04 LTS.

---

### Post by Krytarik on 2012-03-09
> **73ckn797 said:**
> You did not state which version of Ubuntu you were using so I assumed it was 10.04 LTS.
Although that the OP is running at least Oneiric 11.10 is indicated by:
> **crf said:**
> **Alt-rightclick** on the panel
... this:
> **73ckn797 said:**
> I find the info via \\ gconf-editor // under desktop/gnome/background.
... is still:
> **crf said:**
> Is that setting not **for the Desktop [period]**, rather than the panel?
;-) - Regards.

---

