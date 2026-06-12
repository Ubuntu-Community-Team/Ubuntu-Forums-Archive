---
title: "Compiling error help"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by eidauk on 2007-06-28
I've never compiled before, but I tried it on the file [gnome-menu-file-browser-applet.]("http://code.google.com/p/gnome-menu-file-browser-applet/") I followed the author's install instructions, but can't get it to work. I really like this applet and would like to figure out how to install it.

```
root@eidauk-laptop:/home/eidauk/Desktop/menu-file-browser-applet-0.3.0# cmake .
-- Configuring done
-- Generating done
-- Build files have been written to: /home/eidauk/Desktop/menu-file-browser-applet-0.3.0
root@eidauk-laptop:/home/eidauk/Desktop/menu-file-browser-applet-0.3.0# make
[ 50%] Building C object src/CMakeFiles/menu-file-browser-applet.dir/main.o
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:26:21: error: gtk/gtk.h: No such file or directory
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:27:26: error: panel-applet.h: No such file or directory
In file included from /home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:28:
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:29:26: error: glib/gprintf.h: No such file or directory
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:31:35: error: libgnomeui/libgnomeui.h: No such file or directory
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:32:35: error: libgnomevfs/gnome-vfs.h: No such file or directory
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:33:49: error: libgnomevfs/gnome-vfs-mime-handlers.h: No such file or directory
In file included from /home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:28:
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:40: error: expected specifier-qualifier-list before &#8216;GtkWidget&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:44: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gchar&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:44: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:36: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:37: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:38: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:39: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:40: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:41: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_create&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:42: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_factory&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:44: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:56: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_menu_verbs&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:65: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:81: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:97: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:140: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:151: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:159: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_create&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:213: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_factory&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:225: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:226: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PANEL_TYPE_APPLET&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:227: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:228: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:229: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;file_browser_applet_factory&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:230: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;NULL&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:230: warning: return type defaults to &#8216;int&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c: In function &#8216;PANEL_APPLET_BONOBO_FACTORY&#8217;:
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:230: error: expected &#8216;{&#8217; at end of input
make[2]: *** [src/CMakeFiles/menu-file-browser-applet.dir/main.o] Error 1
make[1]: *** [src/CMakeFiles/menu-file-browser-applet.dir/all] Error 2
make: *** [all] Error 2
root@eidauk-laptop:/home/eidauk/Desktop/menu-file-browser-applet-0.3.0# make install
[ 50%] Building C object src/CMakeFiles/menu-file-browser-applet.dir/main.o
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:26:21: error: gtk/gtk.h: No such file or directory
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:27:26: error: panel-applet.h: No such file or directory
In file included from /home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:28:
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:29:26: error: glib/gprintf.h: No such file or directory
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:31:35: error: libgnomeui/libgnomeui.h: No such file or directory
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:32:35: error: libgnomevfs/gnome-vfs.h: No such file or directory
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:33:49: error: libgnomevfs/gnome-vfs-mime-handlers.h: No such file or directory
In file included from /home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:28:
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:40: error: expected specifier-qualifier-list before &#8216;GtkWidget&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:44: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gchar&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/menu-browser.h:44: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:36: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:37: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:38: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:39: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:40: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:41: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_create&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:42: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_factory&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:44: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:56: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_menu_verbs&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:65: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:81: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:97: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:140: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:151: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:159: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_create&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:213: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;file_browser_applet_factory&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:225: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:226: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PANEL_TYPE_APPLET&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:227: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:228: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:229: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;file_browser_applet_factory&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:230: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;NULL&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:230: warning: return type defaults to &#8216;int&#8217;
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c: In function &#8216;PANEL_APPLET_BONOBO_FACTORY&#8217;:
/home/eidauk/Desktop/menu-file-browser-applet-0.3.0/src/main.c:230: error: expected &#8216;{&#8217; at end of input
make[2]: *** [src/CMakeFiles/menu-file-browser-applet.dir/main.o] Error 1
make[1]: *** [src/CMakeFiles/menu-file-browser-applet.dir/all] Error 2
make: *** [all] Error 2
```

I checked to be sure I had all dependencies installed also.

---

### Post by Bachstelze on 2007-06-28
```
sudo apt-get install libgtk2.0-dev
```

Then try to build your thing again :)

---

### Post by eidauk on 2007-06-28
Thanks for the quick reply. I just installed those and compiled again, but the error messages seem to still be the same.

---

### Post by FuturePilot on 2007-06-28
Do you have the build-essential package installed?

---

### Post by eidauk on 2007-06-28
Yes. Version 11.3.

---

