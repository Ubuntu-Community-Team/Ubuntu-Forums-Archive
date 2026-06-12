---
title: "Xubuntu 11.04 + Compiz w/ xfwm4 = Missing Tilebars"
date: 2011-10-31
forum: Desktop Environments
---

### Post by johnathanamber on 2011-10-31
Hey everyone,

I've been trying to get Compiz configured to work with xfwm4/xfce. I want Compiz for their tabbing abilities at this point.

I've already added "xfwm4" under *Command* in _Windows Decorations_ and the same issue happens after running:
```
compiz --replace
```

The titlebars/Windows Decorations go missing.

I've installed the following:
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-plugins
compiz-plugins-extra
compiz-plugins-main
compizconfig-settings-manager
emerald
libdecoration0
libemeraldengine0
python-compizconfig

At this point I've been able to get the titlebars back when running the following command:
```
xfwm4 --replace
```

Any ideas?

Thank you and God bless,
Johnathan

---

### Post by 3Miro on 2011-10-31
You cannot run both compiz and xfwm4, it is one or the other.

Compiz runs well with the rest of Xfce, however, you will have issues with the Windows Decorations. The default compiz decorator uses Gnome Metacity themes and in order to change the theme you will need to install Gnome-Control-Center. 

The command to use the Metacity-like decorator used to be
```
gtk-window-decorator --replace
```
but I think it changed to
```
compiz-decorator --replace
```

---

### Post by johnathanamber on 2011-10-31
Ah, OK, that makes more sense.

I get this when running compiz-decorator --replace:
```
$ compiz-decorator --replace
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
Segmentation fault
```

I also get this when running gtk-window-decorations --replace:
```
gtk-window-decorator --replace
Window manager warning: Failed to load theme "Clearlooks": Failed to find a valid file for theme Clearlooks
```

So I went ahead and installed the following:
gnome-themes-selected
gtk-clearlooks-gperfection2-theme

And now when I run the above 2nd command, nothing happens.

I did install metacity and the following does work however transparancies and some other effects are no longer working:
```
metacity --replace
```

Any ideas?

Basically, I could care less about the themes... all I really want from Compiz is its tabbing options. But I suppose Compiz with its themes has to be running for me to get that option. So here I am.

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2011-10-31
OK, I've removed emerald for now. Now when I run compiz --replace I see the following:
```
$ compiz --replace

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing move options...done
Initializing titleinfo options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing grid options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing staticswitcher options...done
Initializing place options...done
Initializing wall options...done
Initializing blur options...done
Initializing session options...done
Initializing animation options...done
Initializing expo options...done
Initializing workarounds options...done
Initializing fade options...done
Initializing addhelper options...done
compiz (core) - Error: Plugin 'text' not loaded.

Initializing group options...done
Initializing scale options...done
```

The titlebar and decorations are there like when I ran metacity --replace.

I will reboot with compiz --replace running at startup to see what happens.

Thanks again and God bless,
Johnathan

---

### Post by johnathanamber on 2011-11-01
After adding the compiz --replace during boot, I can now see the titlebar.

So, to recap, installing metacity and uninstalling emerald resolved the issue when I ran:
```
compiz --replace
```

Thanks for your help.

Thanks again and God bless,
Johnathan

---

