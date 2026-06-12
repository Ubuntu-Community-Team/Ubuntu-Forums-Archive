---
title: "Compile SCIM/SKIM with anthy?"
date: 2006-02-14
forum: Desktop Environments
---

### Post by Trojan1313 on 2006-02-14
I've compiled there packages so far (top ones first):
anthy-7100
scim-1.4.4
scim-anthy-0.9.0
skim-1.4.4

They all compile fine, then I come to "skim-scim-anthy-0.9.0", and I get this error:
```
scimanthysettingplugin.moc:213:   instantiated from here
/usr/include/kde/kgenericfactory.tcc:167: error: invalid conversion from 'QObject*' to 'QWidget*'
/usr/include/kde/kgenericfactory.tcc:167: error:   initializing argument 1 of 'ScimAnthySettingPlugin::ScimAnthySettingPlugin(QWidget*, const char*, const QStringList&)'
make[2]: *** [scimanthysettingplugin.lo] Error 1
make[2]: Leaving directory `/home/kaminix/Desktop/installation/skim-scim-anthy-0.9.0/setupui'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kaminix/Desktop/installation/skim-scim-anthy-0.9.0'
make: *** [all] Error 2
```
(/home/kaminix/installation is whre I keep the source-folders.)

and when I try to start SCIM (still in KDE though) I can't use ctrl + space to start typing.

When I try and start skim I get this output:
```
Launching a SCIM daemon with Socket FrontEnd...
Loading kconfig Config module ...
Creating backend ...
Launching a SCIM process with x11...
Loading kconfig Config module ...
Creating backend ...
Failed to launch SCIM.
```

What's wrong?

(I know this kind of isn't a Kubuntu problem, but since we don't have SKIM in the repositories I don't think I'm the only one who's going to get this problem, plus it's probably the best way to get japanese input with Kubuntu)

---

