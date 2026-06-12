---
title: "LXDE,Openbox,Precise - make windows default to maximised, how?"
date: 2012-10-31
forum: Desktop Environments
---

### Post by Dreamer Fithp Apprentice on 2012-10-31
I'm trying a very light Precise, built from the mini iso with lxde-core and most of the lxde components and openbox in the 64 bit flavor. Strictly speaking, it's not Lubuntu. It's lighter than that, but it should be pretty close.

How can I make all windows open initially maximised? I realize I could invoke many programs with geometry arguments and even make scripts to open them and point my *.desktop files at the scripts instead of wherever they point now but that seems remarkably inelegant, not to mention a lot of work. 

There must be an easier way. It doesn't HAVE to be ALL windows. I'd settle for a config file with entries for each program I want to specify this behaviour for, for instance.

I'd appreciate any suggestions.

---

### Post by oscarbenjamin on 2012-10-31
I'm new to Lubuntu/LXDE myself so my advice may be incorrect.

I have a file called ~/config/openbox/lubuntu-rc.xml I think this file was there by default after install. It's possible that I copied that file from somewhere in /etc. I've been using that file to create custom keyboard shortcuts and it works for that purpose.

Near to the bottom of the file is a set of commented out xml tags that control default application window settings. One of the commented out tags looks like this:

```
<!-- Option to maximize all normal window when launched-->
<application type="normal">
  <maximized>true</maximized>
</application>
```

If you add a tag like that to your rc.xml file I guess that it will "make windows default to maximised" as desired (I haven't tried myself).


Oscar

---

### Post by Dreamer Fithp Apprentice on 2012-11-01
Thanks, Oscar! That's perfect. For me the equivalent file is lxde-rc.xml in the same location. I put:

```
<application name="*">
    <focus>yes</focus>
    <maximized>true</maximized>
    <decor>yes</decor>
    </application>
```

in there and it did exactly what I wanted. I'll study the "type=", "class=", and "role=" statements and fine tune it some more but this is already a huge improvement.

---

