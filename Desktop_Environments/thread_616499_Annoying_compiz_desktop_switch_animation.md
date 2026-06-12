---
title: "Annoying compiz desktop switch animation"
date: 2007-11-18
forum: Desktop Environments
---

### Post by joeljkp on 2007-11-18
Hello everyone. Is there a way to turn off the annoying "slide" animation in compiz when you switch desktops? I want to keep compiz on, but I want to go back to switching desktops with no animation at all.

Thanks.

---

### Post by mouseboyx on 2007-11-18
in terminal:
```

sudo apt-get install compizconfig-settings-manager

```will install an advanced settings manager for compiz where you can change anything you like

---

### Post by joeljkp on 2007-11-18
> **mouseboyx said:**
> in terminal:
```

sudo apt-get install compizconfig-settings-manager

```will install an advanced settings manager for compiz where you can change anything you like

Yeah, I have that, I just don't see anywhere to turn off the sliding animation. I can turn off desktop switching altogether, but that's not what I want.

---

### Post by duncanyoyo1 on 2007-11-18
On your task bar just add the desktop manager and click to change to different desktops there should be no animation.

---

### Post by joeljkp on 2007-11-18
> **duncanyoyo1 said:**
> On your task bar just add the desktop manager and click to change to different desktops there should be no animation.

I have the "workspace switcher" on my panel, and that's what makes it annoying. Every time I click on another desktop, it does the sliding animation before it goes to it.

---

### Post by mouseboyx on 2007-11-18
in the compiz config turn everything off under the desktop heading

---

### Post by joeljkp on 2007-11-18
> **mouseboyx said:**
> in the compiz config turn everything off under the desktop heading

If I do that I can't switch desktops at all, even by clicking them on the workspace switcher on the panel.

---

### Post by kryth on 2008-01-02
If you figure out how to turn off, let me know please. Because I want to turn it back on. Thanks.

---

### Post by djf_jeff on 2008-01-22
I know it's late but I am in the search of this too.

I want to use compiz but I cannot stand the desktop changing animation.

What I want is to keep compiz on but have no animation when I change desktop with a shortcut or with the panel applet (like in metacity).

---

### Post by pysar on 2008-02-03
I found it very annoying as well. I did the following. In CompizConfig Settings Manager, click on Desktop Wall to view the associated parameters. Go to Viewport Switching tab and set the Wall Sliding Duration to 0.1 (the minimum). Also, on Viewport Switching Preview tab, I unchecked 'Show Viewport Switcher Preview' to remove those annoying squares that appear during switches. It still doesn't feel quite right but at least I don't have vertigo anymore.

---

### Post by pysar on 2008-02-03
I have to take that back :( I played with other settings then reset everything back and now it works as it was before. I don't know what caused the old normal behavior then. I have opted for a cube for now. It's not as bad as Desktop Wall.

---

### Post by JMC_Rimmer on 2008-02-18
> **kryth said:**
> If you figure out how to turn off, let me know please. Because I want to turn it back on. Thanks.

I would love to know how to turn it back on too.

---

