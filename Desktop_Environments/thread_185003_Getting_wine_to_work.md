---
title: "Getting wine to work"
date: 2006-05-30
forum: Desktop Environments
---

### Post by benuski on 2006-05-30
I'm trying to get wine to work so I can run AIM on linux (gaim doesn't let me join chats on the current Ubuntu version).  And I'm running into problems.  I either get 
```
bsbrom@bsbrom:~$ wine aim
wine: could not load L"c:\\windows\\system32\\aim.exe": Module not found
bsbrom@bsbrom:~$ wine c:\\windows\\program files\\aim\\aim.exe
wine: cannot find 'c:\windows\program'

```

Or I get:
```
bsbrom@bsbrom:~$ wine "/media/windows/Program Files/AIM/aim.exe"
err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\oscres.dll") not found
err:module:import_dll Library oscres.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\oscore.dll") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\oscres.dll") not found
err:module:import_dll Library oscres.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\ATE32.dll") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\ATE32.dll") not found
err:module:import_dll Library ATE32.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\oscore.dll") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\oscore.dll") not found
err:module:import_dll Library oscore.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\aim.exe") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\oscres.dll") not found
err:module:import_dll Library oscres.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\aim.exe") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\windows\\Program Files\\AIM\\aim.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\windows\\Program Files\\AIM\\aim.exe" failed, status c0000135

```

Any suggestions? Can I get gaim to work somehow? Can you guys help me get wine to work?

---

### Post by slavik on 2006-05-30
you should give wine the full path to the executable ...

for the dll errors, get a windows system and copy them out (looks like they aren't implemented yet).

---

### Post by RAOF on 2006-05-30
Also, it looks like you're trying to run the AIM installed on your windows partition.  That won't always work, even between copies of Windows.

You should, ideally, first run the AIM installer in wine, then run AIM through wine.

---

### Post by benuski on 2006-05-30
[QUOTE=RAOF]Also, it looks like you're trying to run the AIM installed on your windows partition.  That won't always work, even between copies of Windows.

You should, ideally, first run the AIM installer in wine, then run AIM through wine.[/QUOTE]

How do I do that?

---

### Post by kripkenstein on 2006-05-31
To install aim in wine (that is, inside wine's fake windows C drive), just download the aim installer, and run it in wine. It should install ok (but not all software does).

It is then installed in the fake wine drive, under .wine in your home directory. Btw, you can navigate that drive conveniently (and run programs from it) using the wine file manager, run 'winefile'. Then on the top you can tell it to look in your "C" drive, this is the fake windows drive inside wine.

---

### Post by Bokonon on 2006-05-31
Just a generic comment, but you might try getting a newer version of wine if you are using the default one.  

[wine]("http://www.winehq.org")

You will find information to add to your sources.list or synaptic.  (i386)

On that site's download section, you can also find additional packages to install before you install wine.  There is a dapper script to handle the install for you which makes it easy.

If wine still has trouble, you might consider winetools which you can also find a link for at the downloads section of the site.  I like winetools, but agree with the site that you should try it without winetools if possible.  No big problems with winetools, but you can end up installing quite a lot of unecessary software with it.

I did all that and have the latest version of wine running and most things work well.  Neverwinter nights install went fairly well and media player works great, but IE is failing for me.  I cannot run IE from my windows install via wine either.

---

### Post by kripkenstein on 2006-05-31
Bokonon, two things:

Neverwinter nights has a Linux client - no need for wine! The instructions on the official website are fairly simple. If you have a windows install disc, it tells you how to create a linux install from it. Works great here.

Internet Explorer - the best way, I have found, is to use [ies4linux]("http://www.tatanka.com.br/ies4linux/index-en.html").  Go [here]("http://www.tatanka.com.br/ies4linux/news/") to download the beta, which works great: IE with flash, etc.

---

