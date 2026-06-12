---
title: "Configuring Apache"
date: 2005-11-05
forum: Desktop Environments
---

### Post by fnando on 2005-11-05
Hi!

When I try to access [http://localhost]("http://localhost") I receive the following message:

> 
Not Found 
The requested URL / was not found on this server.
 Apache/2.0.54 (Ubuntu) mod_python/3.1.3 Python/2.4.2 PHP/4.4.0-3 mod_ruby/1.2.4 Ruby/1.8.3(2005-06-23) Server at localhost Port 80


The strange thing is that I was running apache this morning.
Any tip?

---

### Post by fnando on 2005-11-05
Well, I fixed it!

The problem was that I uncommented this lines on apache2.conf

```

#SetHandler mod_python
#AddHandler mod_python .py
#PythonHandler mod_python.cgihandler

```

My error.log has this line:

```

[Sun Nov 06 01:21:33 2005] [error] [client 127.0.0.1] (13)Permission denied: exec of '/media/win_e/dev/feed/rss.py' failed

```

I'm trying to run python script.
How do I do that?

---

