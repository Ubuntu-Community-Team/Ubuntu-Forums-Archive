---
title: "Update Sqlite3 to a newer version"
date: 2011-01-24
forum: Desktop Environments
---

### Post by dolarsrg on 2011-01-24
Hi everyone!

I'm using Ubuntu 8.04LTS and I'm trying to install a ruby gem:

```
# gem install backup              
Building native extensions.  This could take a while...
ERROR:  Error installing backup:
	ERROR: Failed to build gem native extension.

/usr/local/bin/ruby extconf.rb
checking for sqlite3.h... yes
checking for sqlite3_libversion_number() in -lsqlite3... yes
checking for rb_proc_arity()... no
checking for sqlite3_initialize()... no
sqlite3-ruby only supports sqlite3 versions 3.6.16+, please upgrade!
```


It looks like this gem needs a newer version of sqlite3, and it looks like ubuntu comes with:
```
# sqlite3 --version
3.4.2

```

How can I update sqlite3 in a "safe and ubuntu way"?

Thank you very much in advance.

---

### Post by danbirlem on 2011-05-31
I have the same issue as well. Running 8.04LTS and every time I try to update sqlite3-ruby with gem, I get the same version: 3.4.2.

With a little research (I'm lying, it was a lot of research, and I JUST FIGURED IT OUT, WOOT), I found that the transition from 3.4.2 to 3.5.0 in the sqlite3 development was "huge", according to the authors. You can see release notes [here]("http://www.sqlite.org/34to35.html").

With the error message I got (sqlite3-ruby only supports sqlite3 versions 3.6.16+, please upgrade!) I went and looked for source code, version 3.6.16. You can find that version's source code [here]("http://www3.sqlite.org/cgi/src/info/ff691a6b2a").

Compile and install that, then, again, run this command: gem install sqlite3-ruby -v=1.3.0

Most applications I've worked with require sqlite3-ruby v1.3, since it brings the functionality of sqlite3 v3.6.16+. With the additional source from the sqlite3 upgrade, you'll compile the gem with no errors.:popcorn:

---

