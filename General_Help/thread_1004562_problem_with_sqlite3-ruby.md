---
title: "problem with sqlite3-ruby"
date: 2008-12-07
forum: General Help
---

### Post by notgeekenough on 2008-12-07
When I try
```

sudo gem install activerecord sqlite3-ruby

```
I get the following error
```

Select which gem to install for your platform (i486-linux)
 1. sqlite3-ruby 1.2.4 (ruby)
 2. sqlite3-ruby 1.2.3 (x86-mingw32)
 3. sqlite3-ruby 1.2.3 (mswin32)
 4. sqlite3-ruby 1.2.3 (ruby)
 5. Skip this gem
 6. Cancel installation
> 2
Building native extensions.  This could take a while...
ERROR:  While executing gem ... (Gem::Installer::ExtensionBuildError)
    ERROR: Failed to build gem native extension.

ruby extconf.rb install sqlite3-ruby
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
	from extconf.rb:1


Gem files will remain installed in /var/lib/gems/1.8/gems/sqlite3-ruby-1.2.3-x86-mingw32 for inspection.
Results logged to /var/lib/gems/1.8/gems/sqlite3-ruby-1.2.3-x86-mingw32/ext/sqlite3_api/gem_make.out

```

If have already installed sqlite3, libsqlite3-dev. I have tried options 1, 2 and 4 to no avail - getting the same error each time. Has anybody else had these problems.

---

### Post by notgeekenough on 2008-12-07
Never mind, solved it

---

### Post by ugiflezet on 2010-09-05
> **notgeekenough said:**
> Never mind, solved it

please post here how did you solve this?

---

### Post by ugiflezet on 2010-09-06
ok i also got this working:
sudo apt-get install ruby-1.8-dev

---

