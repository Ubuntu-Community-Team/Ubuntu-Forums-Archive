---
title: "[SOLVED] Xmame and Xfce issue"
date: 2007-07-22
forum: Gaming &amp; Leisure
---

### Post by denham2010 on 2007-07-22
Hi All,

Wondering if anyone is able to help!

I am running Debian Etch and up until a short while ago, using Gnome. [EDIT: I know this is the Ubuntu Forums, but Ubuntu being based on Debian and all....plus any other forums I post anything in, I am just ignored - I have never had a single reply to any post except in Ubuntu Forums.]

I installed XMame and GXMame from the repositories, and all worked well.

Recently I have changed over to Xfce for my desktop (still have Gnome - and KDE and Enlightenment for that matter - installed).

When I am in an Xfce session, XMame/GXMame no longer work. GXMame will run and show my ROM list, allow me to make configuration changes and everything as usual, but playing the ROMS will just drop out with an empty error dialogue.

If I log back into a Gnome session, they all work again!

I am unable to post any error messages from the terminal, as I don't get any error messages, also, I have never been able to start a ROM directly from the terminal, nothing happens. I have only ever been able to launch a ROM from GXMame.

Does anyone have any ideas on how I can get this working in an Xfce session?

Thanks.

---

### Post by denham2010 on 2007-07-23
SOLVED

With GXMame, you can set a default directory for the Roms, so when running a rom, you just need to specify the rom name.

It appears under Xfce, the config file which sets this default Rom path is ignored, so GXMame is unable to start any rom unless it is directly in the xmame path.

Instead of using GXMame, I have written script launchers for the roms that use the absolute path to the rom.

All working now!

---

