---
title: "Bastille install problem"
date: 2006-07-29
forum: Desktop Environments
---

### Post by NutrOn on 2006-07-29
When running Bastille command in terminal I get 
         WARNING: /usr/bin/perl cannot find Perl module Tk.
         The above module(s) is/are required to correctly display
         the Bastille User Interface.  If you are unable to find a
         pre-compiled module for your OS, they can be found at:
           [http://www.cpan.org/modules/01modules.index.html](http://www.cpan.org/modules/01modules.index.html)
         If you installed the modules in another installation of
         perl besides the one listed in the error message, you may
         override Bastille's search path by setting the
         $CORRECT_PERL_PATH environment variable to the directory
         that the desired perl binary is located in.
         If you don't want to use the default X11 interface then
         run 'bastille -c'. For more information on available interfaces
         see bastille(1m) or run 'bastille -h
Can anyone clue me in to which mudule I need, exactly?
Thanks,
NutrOn

---

### Post by Fass on 2006-07-29
It seems you need to install perl-tk. It's in the repos.

Looking at the bastille package, it also recommends libgtk-perl, so you might try that one, too, if you want.

---

### Post by nixclusive on 2006-07-29
enter
```
# bastille -c
```

at the prompt for a text (ncurses) interface...works with the default installation.

---

### Post by NutrOn on 2006-07-30
Thanks for the help. I went with the first post as I'm not familiar with C options.
NutrOn

---

### Post by devnulljp on 2006-08-28
You need to install perl-tk and also libgtk-perl if it's not already installed (I use kubuntu, so it wasn't)

```
sudo apt-get install perl-tk libgtk-perl
```

or go with the other poster's recommendation to use ncurses

```

InteractiveBastille -c
```

---

