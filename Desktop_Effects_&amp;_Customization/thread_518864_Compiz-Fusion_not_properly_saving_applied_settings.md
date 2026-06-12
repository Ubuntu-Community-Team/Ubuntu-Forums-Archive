---
title: "Compiz-Fusion not properly saving applied settings"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by airstrike on 2007-08-06
Hello all.

I have sucessfully installed Compiz-Fusion in the past, but this time around it's giving me a few headaches. I believe the last thing I have to adjust is making the CompizConfig Settings Manager successfully apply the settings from the Animation Plugin. I've tried both gconf and flat-file (ini) as the backend and achieved success with neither of them. So after digging (or googling) around, I tried ccsm on the terminal and got a few funny results.

First, I got an error message saying sexy-python wasn't installed. I seem to have installed it properly.

Second, I'm getting tis output whenever I click on the Animations plugin and cycle through its configuration tabs:

```

Initializing animation options...done
/usr/bin/ccsm:2828: GtkWarning: gtk_list_store_get_value: assertion `column < list_store->n_columns' failed
  gtk.main()
/usr/bin/ccsm:2828: Warning: g_object_set_property: assertion `G_IS_VALUE (value)' failed
  gtk.main()
/usr/bin/ccsm:2828: Warning: g_value_unset: assertion `G_IS_VALUE (value)' failed

```

If anyone could enlighten me on the subject I'd be really thankful. Thanks in advance!

---

