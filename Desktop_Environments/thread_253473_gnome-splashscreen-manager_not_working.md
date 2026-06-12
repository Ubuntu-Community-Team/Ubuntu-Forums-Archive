---
title: "gnome-splashscreen-manager not working?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by Griff on 2006-09-08
I used it in Breezy to change my splash screen all the time.  I just recently installed it through apt-get and it isn't able to install any splashes.  Is this working for anybody?  Here's the error output.
```
stephen@stephen-laptop:~$ gnome-splashscreen-manager
/usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `last_writ e': Unrecognized image file format (Gdk::PixbufError)
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192: in `download_pixbuf'
        from /usr/lib/ruby/1.8/open-uri.rb:88:in `open'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:191: in `download_pixbuf'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:199: in `create_thumbnail'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:190: in `install_new_splash_screen'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:173: in `install_new_splash_screen_dialog'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:60:i n `on_button_install_new_splash_screen_clicked'
        from /usr/lib/ruby/1.8/libglade2.rb:44:in `connect'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_man ager.rb:64:in `main'
        from /usr/bin/gnome-splashscreen-manager:25
/usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb: line 192
   GdkPixbuf-WARNING **:GdkPixbufLoader finalized without calling gdk_pixbuf_loa der_close() - this is not allowed. You must explicitly end the data stream to th e loader before dropping the last reference.

```
edit: and i've tried more than one splash from gnome-look

---

### Post by MadTxn on 2006-11-26
Edit: nevermind...

---

### Post by gabrielmenini on 2007-11-05
Hello, there.

I am getting error using Gutsy. Seems to be something about *Gdk::PixbufError*

```
/usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `last_write': Error al interpretar el archivo gráfico JPEG (Application transferred too few scanlines) (Gdk::PixbufError)
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `download_pixbuf'
        from /usr/lib/ruby/1.8/open-uri.rb:32:in `open_uri_original_open'
        from /usr/lib/ruby/1.8/open-uri.rb:32:in `open'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:191:in `download_pixbuf'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:199:in `create_thumbnail'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:271:in `get_splash_screens'
        from /usr/lib/ruby/1.8/rexml/element.rb:934:in `each'
        from /usr/lib/ruby/1.8/rexml/xpath.rb:53:in `each'
        from /usr/lib/ruby/1.8/rexml/element.rb:934:in `each'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:221:in `get_splash_screens'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:261:in `reload_splash_screens'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:458:in `initialize'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_manager.rb:62:in `new'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_manager.rb:62:in `main'
        from /usr/bin/gnome-splashscreen-manager:25

```

---

