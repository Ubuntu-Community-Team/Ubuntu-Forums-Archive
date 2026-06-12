---
title: "Window decoration missing without compiz or emerald"
date: 2008-12-20
forum: General Help
---

### Post by skamarla on 2008-12-20
Hi,

I have a very strange problem. 

On every other login, the window title (the technical name is decoration, right?) is missing. So I log out, back in, and then everything's fine. But the next time I log in, the decoration is missing again?

Anybody has a clue? Some log I can search? I don't need fancy effects; just having the decoration every time would be fine.

I'm running kubuntu hardy; I don't have compiz or emerald even installed at all. My laptop is an Acer Aspire 5315, with an Intel X3100.

Thanks in advance,

---

### Post by nkri on 2008-12-20
Go to System>Preferences>Sessions and check for something that says "compiz --replace" or "emerald --replace"

The above would be in the command box of the properties of the entry.  If it is there, highlight the entry and click Remove.

Good luck!
-nkri

EDIT: sorry, didn't realize you were using KDE...in that case, I don't think I can help:(

---

### Post by Jackelope on 2008-12-20
If its Kubuntu, it should be running Kwin, the KDE window decorator and not emerald or compiz. I'm afraid I'm not much help for the new Kwin decorator, but you could try checking Sessions (or whatever the KDE equivalent is) and see what window decorator is set to start up. You could also try changing the themes to something basic (try the default) and see if that fixes anything.

---

### Post by skamarla on 2008-12-21
I have tried changing themes, even creating a new user, and it's always the same: the window decorations are missing every other time.

I have done some research, and, when decorations are missing, I see the following in my .xsession-errors file
```
Could not find '' executable.
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.
so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.
so: undefined symbol: NP_GetMIMEDescription
kbuildsycoca running...
Reusing existing ksycoca
Could not find 'restricted-manager-kde' executable.
```

and when it works, I get:

```

kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.
so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.
so: undefined symbol: NP_GetMIMEDescription
kbuildsycoca running...
Reusing existing ksycoca
Could not find '' executable.
Could not find 'restricted-manager-kde' executable.
```

The difference is the position of the "could not find '' executable." error. Or perhaps it's something else, who knows?

Any ideas? It's systemwide, and I haven't touched the global kde config, so it must have been some update triggering the error.

Thanks

---

### Post by h725 on 2009-02-06
Hi, i've the same problem, when i open any of office applications, it make mistakes on the windows decoration. Create it on taskbar too, something like an invervese 8 bit color shade for all running tasks.

From terminal:

H725@PC:~$ soffice
[COLOR="Red"]**QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'**[/COLOR]

i'll get this error message.

My PC use Kubuntu 8.10, with KDE 4.2, with compiz and without the same effect. (with oo 2.4 & oo 3.0 too!)

Is OpenOffice a GTK Application? Is it use Qt3 for create window surface? Maybe this is a point to the mistakes?

---

