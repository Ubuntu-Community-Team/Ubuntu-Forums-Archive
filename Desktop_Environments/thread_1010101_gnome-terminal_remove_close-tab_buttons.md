---
title: "gnome-terminal: remove close-tab buttons"
date: 2008-12-13
forum: Desktop Environments
---

### Post by phorminx on 2008-12-13
In general, I prefer gnome over kde. Yet one thing of gnome-terminal annoys me and makes me use konsole instead: with gnome-terminal, the close-tab button is right on the tab itself. Too often, I end up closing the tab when I wanted to select it. So how can I get rid of these close-tab buttons?

Thanks

---

### Post by fubbleskag on 2008-12-13
I don't believe this is possible currently. Last year someone wrote a patch to address this specifically, but ubuntu devs wouldn't touch it unless it was patched by gnome-terminal devs first - who seem to be against the implementation.

---

### Post by phorminx on 2008-12-13
Too bad! I guess I'll continue using konsole just for that!

---

### Post by fubbleskag on 2008-12-13
don't give up hope - even Mr. Shuttleworth himself wants this functionality, so it's only a matter of time while they find a way to implement it without "pissing off upstream" as he eloquently puts it.

[https://wiki.ubuntu.com/TabConsistency](https://wiki.ubuntu.com/TabConsistency)

---

### Post by phorminx on 2008-12-13
Kind of related: I was also annoyed by firefox that comes with such close-tab buttons, too. Yet firefox is configurable:

In about:config search for browser.tabs.closeButtons and give it the value 3, which will give you one close button for all tabs on the very right of the tabs bar. I believe that seamonkey does that by default.

---

### Post by wdoekes on 2009-03-24
Indeed, it bothered me too. So I came up with this hack. It does the same as Firefox's browser.tabs.closeButtons=0:

```

--- gnome-terminal-2.22.1-orig/src/terminal-screen.h    2008-03-20 11:16:25.000000000 +0100
+++ gnome-terminal-2.22.1/src/terminal-screen.h 2009-03-24 13:26:17.000000000 +0100
@@ -47,6 +47,7 @@
   GtkBin parent_instance;
 
   TerminalScreenPrivate *priv;
+  GtkWidget *close_button;      /* Hide tab close button hack */
 };
 
 struct _TerminalScreenClass
--- gnome-terminal-2.22.1-orig/src/terminal-window.c    2008-03-20 11:16:25.000000000 +0100
+++ gnome-terminal-2.22.1/src/terminal-window.c 2009-03-24 13:36:02.000000000 +0100
@@ -1442,6 +1445,10 @@
 
   gtk_widget_show_all (hbox);
 
+  /* Hide tab close button hack */
+  screen->close_button = close_button;
+  gtk_widget_hide(close_button);
+
   return hbox;
 }
 
@@ -1645,6 +1652,10 @@
   if (window->priv->active_term == screen)
     return;
   
+  /* Hide tab close button hack */
+  if (window->priv->active_term != NULL)
+    gtk_widget_hide(window->priv->active_term->close_button);
+  
   /* Workaround to remove gtknotebook's feature of computing its size based on
    * all pages. When the widget is hidden, its size will not be taken into
    * account.
@@ -1668,6 +1679,10 @@
 
   window->priv->active_term = screen;
 
+  /* Hide tab close button hack */
+  if (window->priv->active_term != NULL)
+    gtk_widget_show(window->priv->active_term->close_button);
+
   terminal_window_update_geometry (window);
   terminal_window_update_icon (window);


```
(licensed in whatever the license-form of gnome-terminal is)


Or you could fetch a pre-deb'd i386 version for hardy here:

[http://wjd.nu/files/2009/03/gnome-terminal_2.22.1-0ubuntu2hideclosebutton_i386.deb](http://wjd.nu/files/2009/03/gnome-terminal_2.22.1-0ubuntu2hideclosebutton_i386.deb)

(copy-paste the url in your browser, my site does referer-checking)


Greetings,
Walter Doekes
OSSO B.V.

---

