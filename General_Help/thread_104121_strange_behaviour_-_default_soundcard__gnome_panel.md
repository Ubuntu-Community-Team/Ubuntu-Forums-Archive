---
title: "strange behaviour - default soundcard / gnome panel"
date: 2005-12-15
forum: General Help
---

### Post by pelle.k on 2005-12-15
Hi all.
Im using the last binary (1.0.5) of the last.fm player. It works (i dont know why, because it usually dont, but hey...) if i launch it from terminal or nautilus (it starts using /dev/dsp)

The odd behaviour is; when i try to launch it from the panel, it uses dsp1 instead of dsp (because dsp is already in use, was the terminal output when i chose launch as "terminal" instead of "application").
/dev/dsp1 is my other sound card, and i don't want to turn it off because - it's my skype phone!...

my internal soundcard (/dev/dsp) is marked as default in "sound preferences".

Why does it use dsp, from nautilus/terminal, but dsp1 when launched from gnome-panel?

---

