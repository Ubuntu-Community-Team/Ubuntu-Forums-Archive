---
title: "Customizing Unity Dash"
date: 2014-08-24
forum: Desktop Environments
---

### Post by bizhat on 2014-08-24
I modified Unity Dash so it only show me applications. I don't want music, videos, folders, files etc..

I got it working.. But Home tab in my Unity Dash is now empty.

I know unity --reset can make it work like default, but that is lot of useless items in dash for me.

**Empty Home Dash**

[[IMG]http://i.imgur.com/L8CAQlKl.png[/IMG]](http://imgur.com/L8CAQlK)

**Search Works in Home Dash**

[[IMG]http://i.imgur.com/Vm2PWZ5l.png[/IMG]](http://imgur.com/Vm2PWZ5)

**Application Dash works**

[[IMG]http://i.imgur.com/1xQLchGl.png[/IMG]](http://imgur.com/1xQLchG)

I want "Most used Applications" shows on Home Dash Screen.

Most used applications, that can be auto generated or it can pinned application (selected me me) like in Windows 7.

Is this possible ? I goggled for "Most used applications" i can see some screenshot of old version of Ubuntu showing this, but can't find how to get that working in Ubuntu 14.04.

---

### Post by mihoo on 2015-03-25
Same here i solved this with dconf.
Under desktop -> unity -> lenses -> applications check option "display-recent-apps"
Hope this helps. :)
M.

---

### Post by bizhat on 2015-03-26
Already have  it enabled.

[IMG]http://i.imgur.com/HcZ3uxo.png[/IMG]

But for some reason, it is not working. It may be i messed up something.. now i get used to it lol

---

### Post by CantankRus on 2015-03-26
Are you still Recording file and application activity in Security and Privacy.
Is zeitgeist running...
```
ps axu |grep [z]eitgeist
```

---

### Post by bizhat on 2015-03-26
I have these running

```

boby@fwhlin:~ $ ps axu |grep [z]eitgeist
boby      3572  0.0  0.0 331400  2692 ?        Sl   08:26   0:00 /usr/bin/zeitgeist-daemon
boby      3578  0.0  0.0 233316  2940 ?        Sl   08:26   0:00 /usr/lib/x86_64-linux-gnu/zeitgeist-fts
boby      3581  0.0  0.0 591212  5232 ?        Sl   08:26   0:01 zeitgeist-datahub
boby@fwhlin:~ $ 

```

---

### Post by CantankRus on 2015-03-26
I do the same except I don't remove unity-lens-files.
The dash Home now **only** shows recently used applications and files.
I find not everything shows in recently used applications but actually starting it from the dash applications seems to be a factor
in whether it shows in dash home as recently used.

Note in the second attached pic of the Application lens it shows "Recently used" before the "Installed".

---

### Post by mihoo on 2015-03-26
Hm... Maybe somethings else...
My settings in dconf are:
com.canonical.Unity.Dash -> ['home.scope', 'applications.scope']
com.canonical.Unity.Lenses - allways-search ->  ['applications.scope']
com.canonical.Unity.Lenses - disabled-scopes -> ['files-local.scope']
com.canonical.Unity.Lenses - home-lens-priority -> ['applications.scope']
com.canonical.Unity.Lenses - remote-content-search -> ['none']

com.canonical.Unity.ApplicationsLens - display-recent-apps -> checked

Everything else i have empty or unchecked. For me problem was solved by "com.canonical.Unity.ApplicationsLens - display-recent-apps" 
Maybe you have zeitgeist off or some thing like that under System settings -> Privacy & security, but i think You checked this already.
Seriously i don't have any idea why dconf not working for You. :(

---

### Post by bizhat on 2015-03-26
Thank you CantankRus and mihoo for the help.

My settings are

```

boby@fwhlin:~ $ gsettings list-recursively | grep com.canonical.Unity
com.canonical.Unity.Dash scopes ['home.scope', 'applications.scope', 'files.scope', 'video.scope', 'music.scope', 'photos.scope', 'social.scope']
com.canonical.Unity integrated-menus false
com.canonical.Unity double-click-activate true
com.canonical.Unity minimize-slow-duration 800
com.canonical.Unity minimize-fast-duration 300
com.canonical.Unity form-factor 'Automatic'
com.canonical.Unity home-expanded 'Expanded'
com.canonical.Unity minimize-count 0
com.canonical.Unity minimize-speed-threshold 100
com.canonical.Unity.FilesLens use-locate true
com.canonical.Unity.Interface text-scale-factor 1.0
com.canonical.Unity.Interface app-scale-factor-monitor ''
com.canonical.Unity.Interface cursor-scale-factor 1.0
com.canonical.Unity.Interface app-fallback-to-maximum-scale-factor true
com.canonical.Unity.Runner history @as []
com.canonical.Unity.Devices blacklist ['8b269653-7fae-4260-ae29-9750ce5f9384-part_data']
com.canonical.Unity.ApplicationsLens display-available-apps true
com.canonical.Unity.ApplicationsLens display-recent-apps true
com.canonical.Unity.Decorations grab-wait uint32 175
com.canonical.Unity.Launcher favorites ['application://ubiquity.desktop', 'application://nautilus.desktop', 'application://firefox.desktop', 'application://ubuntu-amazon-default.desktop', 'unity://running-apps', 'unity://expo-icon', 'unity://devices']
com.canonical.Unity.Launcher favorite-migration ''
com.canonical.Unity.Lenses home-lens-priority ['files.scope', 'music.scope']
com.canonical.Unity.Lenses disabled-scopes @as []
com.canonical.Unity.Lenses remote-content-search 'all'
com.canonical.Unity.Lenses home-lens-default-view ['applications.scope', 'files.scope']
com.canonical.Unity.Lenses hidden-scopes @as []
com.canonical.Unity.Lenses always-search ['applications.scope', 'music.scope', 'videos.scope', 'files.scope']
com.canonical.Unity.Lenses locked-scopes @as []
com.canonical.Unity.IntegratedMenus click-movement-threshold uint32 15
com.canonical.Unity.IntegratedMenus double-click-wait uint32 0
boby@fwhlin:~ $ 

```

Most of them are default, i changes all of these to default values.

I don't see a key with name "com.canonical.Unity.ApplicationsLens"

> **mihoo said:**
> 
Maybe you have zeitgeist off or some thing like that under System settings -> Privacy & security, but i think You checked this already.


I think this one...

[img]http://i.imgur.com/Y9EfwCv.png[/img]

This is how it was, so i am changing it to "ON",  hope this will fix the problem :)

---

### Post by mihoo on 2015-03-31
Yes this settings put this ON. I hope this is it ;)

You can Uncheck everything else ad add your hdd as exluded on the right because you have only apps in dash.
Mark as solved if everything is fine ;)
Cheers :)

---

