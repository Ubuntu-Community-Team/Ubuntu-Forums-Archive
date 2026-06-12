---
title: "GNOME Splash Screen Manager CRASH"
date: 2006-08-11
forum: Desktop Environments
---

### Post by rykel on 2006-08-11
Dear friend,

Perhaps you can help me? I cannot start up GNOME Splash Screen Manager... using Ubuntu Dapper Drake, fully updated to 6.06.1 LTS.

Cheers.

[INDENT][B]~$ gnome-splashscreen-manager
/usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `last_write': Unrecognised image file format (Gdk::PixbufError)
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `download_pixbuf'
        from /usr/lib/ruby/1.8/open-uri.rb:88:in `open'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:191:in `download_pixbuf'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:199:in `create_thumbnail'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:271:in `get_splash_screens'
        from /usr/lib/ruby/1.8/rexml/element.rb:939:in `each'
        from /usr/lib/ruby/1.8/rexml/xpath.rb:53:in `each'
        from /usr/lib/ruby/1.8/rexml/element.rb:939:in `each'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:221:in `get_splash_screens'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:261:in `reload_splash_screens'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:447:in `initialize'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_manager.rb:62:in `main'
        from /usr/bin/gnome-splashscreen-manager:25
[/B][/INDENT]

---

### Post by simple2000 on 2007-03-27
I had the same problem, and looked all over for the answer. I don't know if it will work for you but what happened for me was that gnome-art downloaded a wrongly formatted file: Splash-CountrySplash.png into the splash directory (~/.gnome2/gnome-art/download/splashscreens.) I deleted the file and everything worked fine.

---

### Post by mnichau on 2008-03-06
I had exactly the same problem with the splash manager in Gutsy - same output in the terminal as rykel, and the same broken png file that simple2000 has reported, i.e. Splash-CountrySplash.png.

I looked into this broken png file and it looks like it hadn't been retrieved correctly:

<html><head>

<title></title></head>
<!-- Redirection Services Redirector2B-DAL H1 -->
<frameset rows='100%, *' frameborder=no framespacing=0 border=0>
<frame src="http://clientes.netvisao.pt/spookyftp/files/splah.png" name=mainwindow frameborder=no framespacing=0 marginheight=0 marginwidth=0></frame>
</frameset>
<noframes>
<h2>Your browser does not support frames.  We recommend upgrading your browser.</h2><br><br>
<center>Click <a href="http://clientes.netvisao.pt/spookyftp/files/splah.png">here</a> to enter the site.</center>
</noframes></html>


Obvoiusly it's not what  a png file should have inside.
I removed it and the splash manager works fine agian, i.e. doen't crash on start.

I think it's a bug and i'll try to report it, as i don't think the manager should crash on a broken file - it shouldn't actually save it in the first place.
On the other hand, this particular file (Splash-CountrySplash.png) should probably be unlisted from the manager (or from the server that the  list of splash screens is retrieved from).

---

