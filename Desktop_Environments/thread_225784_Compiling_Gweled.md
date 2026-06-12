---
title: "Compiling Gweled"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Afief on 2006-07-30
Hello Everybody,
I have been able to compile quite a number of packages and they all work flawlessly for me, today i compiled Gweled but when i run it the window appears but nothing functions(and the jewls don't appear either)

This is the console output i get:

```
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(gweled:24438): libglade-WARNING **: could not find signal handler 'drawing_area_button_event_cb'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_scores1_activate'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_app1_delete_event'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_preferences1_activate'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_quit1_activate'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_smallRadiobutton_toggled'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_highscoresDialog_delete_event'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_about1_activate'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'drawing_area_motion_event_cb'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_preferencesDialog_delete_event'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_closebutton1_clicked'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_new1_activate'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'drawing_area_expose_event_cb'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_mediumRadiobutton_toggled'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_easyRadiobutton_toggled'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_hardRadiobutton_toggled'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_closebutton2_clicked'.

(gweled:24438): libglade-WARNING **: could not find signal handler 'on_largeRadiobutton_toggled'.

```

Does anybody know what this means and/or how this it can be fixed? it's the first time i see this

---

### Post by ardchoille on 2006-07-30
Is there a specific reason you are compiling gweled? I ask that because gweled is in the universe repo. Enable the universe repo and you can install it with:

```

sudo apt-get install gweled

```

---

### Post by hmagoo on 2006-07-31
I have the same problem, installed a ton of packages that I thought might be causing the problem and I get the same error.  I built it first, then realized it was in the repositories so I installed the package as well.  Nothing changes.

hmm, Edit: looks like if I go to usr/games it works.  perhaps I am executing the compiled version somehow otherwise.  anywho, I'm ok with this.

---

