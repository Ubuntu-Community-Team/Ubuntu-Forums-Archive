---
title: "Default session per user"
date: 2007-06-20
forum: Desktop Environments
---

### Post by Foxmike on 2007-06-20
Hi!  I got a little anoyance here.  It is not a big deal but still, if I could get help to get it resolved...

I used to use GNOME as a default DE, and so my girlfriend.  I am now migrating to KDE as most of the applications I use are KDE based and I begin to really enjoy this DE (at least for now) and I would like to make it a default for me, but for me only so then I wouldn't have to manually select "KDE session" each time I log in, but I want GNOME to stay the default DE for my girlfriend so she will not complain about everything being different (again...):)  I have looked to man pages of GDM, KDM, xsessions, xinit, but I am still unsure of the proper way to do this (if it is possible...).

I am sure there is a way to get it done, I am just not sure where to look..

Thanks in advance!:)

Regards,
-FM

---

### Post by Happy_Man on 2007-06-20
Sorry, bud, not that I know of.... glad to see a fellow Ubuntuian come across the sea to K province. Hope you like the view! (It's not all brown and muddy like over in Ubuntu province, either. :D)

---

### Post by Foxmike on 2007-06-21
Well, it is not my first attempt to use KDE as default, but I must say that the default layout is a bit too bright to me, so I have played a bit with colors/style/icons to get something a bit smoother.  While I like the overall "customability" of KDE, I found that Beryl still doesn't work well with it (example: when I logout, the "color-fade" is preceeded by a kind of blank that takes out all the windows, even the logout window, so I have to re-activate Kwin in order to be able to select the logout option...), but this is ok since Beryl is quite heavy on my celeron 1.7GHz/nvidia 6200.
 
I must say that KDE apps really rocks!  Digikam, kmymoney, kate, amarok...
 
Anyway, thanks for the info, tho I thought that getting a ~/.xsession file or something like that would help, but as I said, I was not sure how to manage it.
 
Regards,
 
-FM

---

### Post by technofreak_in on 2007-08-22
Hi,

Check the ~/.dmrc file. You can set your per-user default session in this config file :)

---

### Post by Foxmike on 2007-08-24
Kool, thank you very much!:)  Aside of that, I just realised that KDM seems to already do such thing: when you select a DE for your username, by default it will load that DE each time you re-login, but that doesn't seem to change other users's default!

I'll check that tonight when getting back from work!:)

---

