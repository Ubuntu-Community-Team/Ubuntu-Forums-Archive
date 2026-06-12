---
title: "Splash Screen Manager Broken"
date: 2007-12-23
forum: Desktop Effects &amp; Customization
---

### Post by rhibberd on 2007-12-23
I have broken my Splash Screen Manager.  When I run gnome-splashscreen-manager in terminal, I get the following:

raymond@Big-PC:~$ gnome-splashscreen-manager
/usr/bin/gnome-splashscreen-manager: line 22
   Gtk-WARNING **:Theme directory 48x48/mimetypes of theme Snow-Apple has no size field

/usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `last_write': Error interpreting JPEG image file (Application transferred too few scanlines) (Gdk::PixbufError)
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
raymond@Big-PC:~$ 

 
I think there is a problem with one (or more) splash screens that I have downloaded or in splash manager's setting file.  How do reset/fix splash manager?

I have already tried uninstall/reinstall splash manager. 

I am running Gusty.  

Also splash  manager works in other logins.

Thanks for any help.

---

### Post by rhibberd on 2007-12-24
bump

---

### Post by rhibberd on 2007-12-28
Bump II

---

### Post by rhibberd on 2008-01-02
Bump III

Now that people ares back from vacation.  Someone can answer my problem.

---

