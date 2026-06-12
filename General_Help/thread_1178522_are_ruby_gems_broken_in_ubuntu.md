---
title: "are ruby gems broken in ubuntu?"
date: 2009-06-04
forum: General Help
---

### Post by Locke2053 on 2009-06-04
This could be user error (if so, the UI is partially to blame!) but I can't get ruby gems working properly with ubuntu. The same problem happens on both 8.04 and 9.04.

To use ruby with MSSQL, you need the ODBC driver. You get this by doing:
```
sudo gem install dbi
sudo gem install dbd-odbc
```

These commands execute without errors in ubuntu, but then when you try to load dbi from within a ruby program, you get:
```
LoadError: no such file to load -- dbi
```

Now, I did get this working in ubuntu by using
```
sudo apt-get install libodbc-ruby
```

But I would hope the gem system would work properly on ubuntu; there are many gems which aren't available through apt.

Anyone know what's up? I've had no gem problems on windows--just on ubuntu.

---

