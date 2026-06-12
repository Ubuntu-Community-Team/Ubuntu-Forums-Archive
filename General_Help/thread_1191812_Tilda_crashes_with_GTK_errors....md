---
title: "Tilda crashes with GTK errors..."
date: 2009-06-19
forum: General Help
---

### Post by ThinkBuntu on 2009-06-19
In Ubuntu 8.04 LTS I installed Tilda to have a nice drop-down terminal, but it crashes on start:

```

% tilda             

(tilda:7699): Gtk-CRITICAL **: gtk_file_chooser_select_filename: assertion `filename != NULL' failed

(tilda:7699): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed
zsh: segmentation fault  tilda

```

I don't know much about GTK or C, but what do these errors indicate...how can I fix this?

---

### Post by VCoolio on 2009-06-19
Dunno how to fix your issue, but try guake, same idea, maybe that works. I used it for a time, worked fine.

---

