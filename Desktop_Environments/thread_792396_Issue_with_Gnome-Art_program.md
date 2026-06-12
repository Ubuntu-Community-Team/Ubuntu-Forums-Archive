---
title: "Issue with Gnome-Art program"
date: 2008-05-12
forum: Desktop Environments
---

### Post by damonjablons on 2008-05-12
I installed gnome-art but it won't run.  If i try to run it via terminal, i get this output:

```

$ gnome-art
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier `tooltip_bg_color', expected valid identifier
/usr/lib/ruby/1.8/net/protocol.rb:133:in `sysread': Connection reset by peer (Errno::ECONNRESET)
	from /usr/lib/ruby/1.8/net/protocol.rb:133:in `rbuf_fill'
	from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
	from /usr/lib/ruby/1.8/net/protocol.rb:132:in `rbuf_fill'
	from /usr/lib/ruby/1.8/net/protocol.rb:116:in `readuntil'
	from /usr/lib/ruby/1.8/net/protocol.rb:126:in `readline'
	from /usr/lib/ruby/1.8/net/http.rb:2020:in `read_status_line'
	from /usr/lib/ruby/1.8/net/http.rb:2009:in `read_new'
	 ... 10 levels...
	from /usr/lib/ruby/1.8/open-uri.rb:30:in `open'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:156:in `isConnected'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
	from /usr/bin/gnome-art:25

```

how do i fix this?

thanks!

---

### Post by damonjablons on 2008-05-13
anyone have any clues?

---

### Post by koma77 on 2008-05-13
Just wanted to say that I have the same problem.

I think you should file a bug report.

---

### Post by OlegVekhov on 2008-05-14
Yes! This problem exist in x32 and x64 versions of 8.04 Ubuntu!
```
/usr/lib/ruby/1.8/net/protocol.rb:133:in `sysread': Connection reset by peer (Errno::ECONNRESET)
	from /usr/lib/ruby/1.8/net/protocol.rb:133:in `rbuf_fill'
	from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
	from /usr/lib/ruby/1.8/net/protocol.rb:132:in `rbuf_fill'
	from /usr/lib/ruby/1.8/net/protocol.rb:116:in `readuntil'
	from /usr/lib/ruby/1.8/net/protocol.rb:126:in `readline'
	from /usr/lib/ruby/1.8/net/http.rb:2020:in `read_status_line'
	from /usr/lib/ruby/1.8/net/http.rb:2009:in `read_new'
	 ... 21 levels...
	from /usr/local/lib/site_ruby/1.8/gnome-art/gnome_art.rb:132:in `call'
	from /usr/local/lib/site_ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
	from /usr/local/lib/site_ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
	from /usr/bin/gnome-art:25

```

---

