---
title: "How does lightdm determine which sessions to show as options?"
date: 2012-01-12
forum: Desktop Environments
---

### Post by jejones3141 on 2012-01-12
I switched to a ppa to get an up-to-date and complete E17 including some packages to let removable devices be detected and automounted--and after doing that, I no longer see enlightenment as a possible choice of session.

UPDATE: It helps to install all the pertinent packages.

Here's what I've determined so far:

[LIST]
[*]/usr/share/xsessions contains a file named enlightenment.desktop, which, as far as I can tell, looks reasonable.
[*]/var/lightdm/x-0-greeter.log contains a line saying it's ignoring the enlightenment.desktop file.
[/LIST]
So... what is it that determines whether a particular session is shown as a choice under lightdm? There are other files that are ignored. I could see ignoring the guest sessions when I, a non-guest, log in (BTW, if one wants to give a guest other window manager options, how is that done?), and gnome.desktop is ignored (its Name= value is the same as another file, ubuntu.desktop, but if that is the reason it's ignored, why does gnome.desktop appear first in the log file?) AfterStep.desktop is ignored as well, so I will look for commonalities between it and enlightenment.desktop, but I'd appreciate any pointer to info on what determines whether a given session is listed or not.

---

### Post by jejones3141 on 2012-01-12
More info: I notice that some of the .desktop files contain either

NoDisplay=true

or

Hidden=true

I'll see whether getting rid of NoDisplay=true makes the AfterStep option appear, but enlightenment.desktop contains neither of those. Its contents follow:

[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Name[ru]=Enlightenment
Name[el]=Enlightenment
Name[eo]=Enlightenment
Name[tr]=Enlightenment
Comment=Log in using Enlightenment (Version 0.16.999.0)
Comment[ru]=&#1042;&#1086;&#1081;&#1090;&#1080; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1103; Enlightenment (&#1042;&#1077;&#1088;&#1089;&#1080;&#1103; 0.16.999.0)
Comment[el]=&#917;&#943;&#963;&#959;&#948;&#959;&#962; &#956;&#949; &#964;&#959; Enlightenment (&#904;&#954;&#948;&#959;&#963;&#951; 0.16.999.0)
Comment[eo]=Ensaluti pere de Enlightenment (Versio 0.16.999.0)
Comment[fr]=Ouvrir une session Enlightenment (Version 0.16.999.0)
Comment[it]=Accedi con Enlightenment (Versione 0.16.999.0)
Comment[pt]=Inicie a sessão com o Enlightenment (Versão 0.16.999.0)
Comment[tr]=Enlightenment kullanarak giri&#351; ya&#305;n (Version 0.16.999.0)
Comment[ko]=Enlightenment &#47196;&#44536;&#51064;(&#48260;&#51204; 0.16.999.0)
Type=XSession
Icon=/usr/share/enlightenment/data/images/enlightenment.png
Exec=/usr/bin/enlightenment_start
TryExec=/usr/bin/enlightenment_start

---

### Post by Krytarik on 2012-01-12
> **jejones3141 said:**
> 
```
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Name[ru]=Enlightenment
Name[el]=Enlightenment
Name[eo]=Enlightenment
Name[tr]=Enlightenment
Comment=Log in using Enlightenment (Version 0.16.999.0)
Comment[ru]=&#1042;&#1086;&#1081;&#1090;&#1080; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1103; Enlightenment (&#1042;&#1077;&#1088;&#1089;&#1080;&#1103; 0.16.999.0)
Comment[el]=&#917;&#943;&#963;&#959;&#948;&#959;&#962; &#956;&#949; &#964;&#959; Enlightenment (&#904;&#954;&#948;&#959;&#963;&#951; 0.16.999.0)
Comment[eo]=Ensaluti pere de Enlightenment (Versio 0.16.999.0)
Comment[fr]=Ouvrir une session Enlightenment (Version 0.16.999.0)
Comment[it]=Accedi con Enlightenment (Versione 0.16.999.0)
Comment[pt]=Inicie a sessão com o Enlightenment (Versão 0.16.999.0)
Comment[tr]=Enlightenment kullanarak giri&#351; ya&#305;n (Version 0.16.999.0)
Comment[ko]=Enlightenment &#47196;&#44536;&#51064;(&#48260;&#51204; 0.16.999.0)
**Type=XSession**
Icon=/usr/share/enlightenment/data/images/enlightenment.png
Exec=/usr/bin/enlightenment_start
TryExec=/usr/bin/enlightenment_start
```
Apart from the "NoDisplay" and "Hidden" keys, both of which shouldn't be set to "true", according to the Desktop Entry Specification "XSession" is not a valid value for "Type", it should be "Application" instead:

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#recognized-keys](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#recognized-keys)

Regards.

---

### Post by jejones3141 on 2012-01-12
> **Krytarik said:**
> Apart from the "NoDisplay" and "Hidden" keys, both of which shouldn't be set to "true", according to the Desktop Entry Specification "XSession" is not a valid value for "Type", it should be "Application" instead:

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#recognized-keys](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#recognized-keys)

Regards.

Thank you! It turns out that my real problem lay elsewhere; I had not installed a needed package that I can't believe I overlooked, i.e. e17 itself. In any case, I have learned more about .desktop files.

---

