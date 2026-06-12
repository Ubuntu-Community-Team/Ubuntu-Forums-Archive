---
title: "Apache2 &amp; First Ruby Script"
date: 2006-09-13
forum: Desktop Environments
---

### Post by atraeyu on 2006-09-13
According to [ProgrammingRuby]("http://www.ruby-doc.org/docs/ProgrammingRuby/html/web.html")  :
*You can use Ruby to write CGI scripts quite easily. To have a Ruby script generate HTML output, all you need is*
```

#!/usr/bin/env ruby
print "HTTP/1.0 200 OK\r\n"
print "Content-type: text/html\r\n\r\n"
print "<html><body>Hello World!</body></html>\r\n"

```

I have a fresh install of ubuntu, almost no experience with apache, cgi, or ruby, but a lot of patience.

I haven't modified my apache2 config, I haven't installed any extra apache-ruby modules.  

If you go to [http://atraeyu.org/](http://atraeyu.org/) you'll notice a ruby.htm file.
Obviously this won't execute.  I'm wondering what I need to do to make it execute.

Do I need to install to install an apache module?  Can I simply change the extension and set it to executable?

I imagine there are a few simple concepts I really don't understand that I need to.  
I will really appreciate any help.  Thanks.

---

