---
title: "Installing ruby-dbi?"
date: 2006-01-12
forum: Desktop Environments
---

### Post by flickerfly on 2006-01-12
I'm trying to install ruby-dbi and running into a problem that I can't seem to work out. I run config fine. Then in setup I get this error. I've messed around with some of the config option mentioned and not come up with a good resolution. Any help or suggestions on getting this working would be appreciated.

```
~/ruby-dbi-all$ ruby setup.rb setup
setup.rb:586: warning: parenthesize argument(s) for future version
setup.rb:720: warning: don't put space before argument parentheses
entering setup phase...
setting #! line to "#!/usr/bin/ruby"
setting #! line to "#!/usr/bin/ruby"
/usr/bin/ruby extconf.rb
checking for sqlite_open() in -lsqlite... no
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
        --with-opt-dir
        --with-opt-include=${opt-dir}/include
        --with-opt-lib=${opt-dir}/lib
        --with-make-prog=make
        --srcdir=.
        --curdir
        --ruby=/usr/bin/ruby
        --with-SQLite-dir=/usr/local
        --with-SQLite-include=${SQLite-dir}/include
        --with-SQLite-lib=${SQLite-dir}/lib
        --with-sqlitelib=sqlite
setup failed
'system /usr/bin/ruby extconf.rb' failed
try "ruby setup.rb --help" for usage

```

---

### Post by Sef on 2006-01-12
If you are installing by source, did you first download build-essential?  If you don't download them, you can configure, but it won't make.

From the terminal:  sudo apt-get install build-essential

---

### Post by oakz on 2006-01-12
The configure script cannot find the sqlite development libraries, if you haven't already installed it, do this:

$ sudo apt-get install libsqlite0-dev

Another thing to look our for is the package is looking for the sqlite libraries and header files starting at /usr/local (look in the "Provided configuration options" in your output). I think apt-get will install the sqlite development files in /usr, not /usr/local/, so you may need to alter the configure script to point at the correct location.

---

### Post by flickerfly on 2006-01-12
That's what it was. Thanks oakz. I ran into another error after that, but 'ruby setup.rb config --without=dbd_sybase' took care of it.

Sef, I'd tried that already. Thanks for checking.

---

