---
title: "Ubuntu Screen Resolution"
date: 2008-04-12
forum: Desktop Environments
---

### Post by robokaso on 2008-04-12
displayconfig-gtk should be what you are looking for. There should also be some new screen resolution utility in hardy - I've just upgraded but can't see it anywhere :(

---

### Post by captainneb on 2008-04-14
In hardy the tool is "System - Preferences - Screen Resolution"  This does not affect the login resolution however.

---

### Post by go_lanche on 2008-04-15
I can run displayconfig-gtk just fine but nothing happens when I select a new resolution. When I click OK I get the dialogue box that asks if I want to keep my new configuration, but the screen resolution is the exact same. Nothing happens if I let it revert and nothing happens if I click OK.

---

### Post by b3nw on 2008-04-15
after setting a new screen resolution in the tool (the tool has wrecked my xorg.conf several times, so I would advise backing it up manually before doing anything) the quickest way to have it take effect is to control+alt+backspace, which will // kill // your current X session. (you will loose anything you were working on). GDM will automagically restart and pickup the new configuration.

---

