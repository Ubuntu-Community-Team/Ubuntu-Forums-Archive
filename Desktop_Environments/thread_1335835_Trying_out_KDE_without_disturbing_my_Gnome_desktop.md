---
title: "Trying out KDE without disturbing my Gnome desktop..."
date: 2009-11-23
forum: Desktop Environments
---

### Post by humphreybc on 2009-11-23
I have Ubuntu Karmic with the Gnome desktop all configured to my liking, it looks great and I don't wish to screw anything up.

One thing that I've noticed is that often KDE programs are of a higher quality than Gnome equivalents - such as kdenlive to Pitivi, digiKam to F-Spot, and k3b to Brasero.

They often have a lot more options and settings which suits me great.

Unfortunately, when running these under Gnome, they use an exorbant amount of RAM - digiKam uses almost 1GB!

So I have been thinking of trying out the KDE environment. How can I set up my computer to keep Gnome as the default session, and then have KDE as another session?

Will I have all the KDE default apps doubled up in my menu in Gnome, and all the Gnome apps in KDE, or will they stick to their own sessions?

Cheers

P.S I don't know much about KDE - what are the benefits of using KDE over Gnome? Or vice versa?

---

### Post by jerrrys on 2009-11-24
I installed KDE to gnome and got seriously dumped on with many apps in my menu.  Can you create maybe a 10gig partition and run it that way?

have you seen this?

[http://www.google.com/search?q=install+kde+to+gnome+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=install+kde+to+gnome+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by Jim_in_Germany on 2009-11-26
> **jerrrys said:**
> I installed KDE to gnome and got seriously dumped on with many apps in my menu.

I can second that. Your menus get ram jammed full of apps, plus my mouse pointer changed from the default gnome pointer to the default kde pointer. Only a small point, but still a bit annoying.

Saying that, [http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde") seems to offer a good explanation of how to do what you want.

However,  be warned! It is quite difficult to undo all of the changes you make to your machine as the kde desktop packet is a so-called meta-packet (ie contains loads of packets itself), so down the road typing "sudo apt-get remove kde-desktop", won't work.

Also, don't follow the advice offered here. A sure fire way to cripple your system:
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by Zorael on 2009-11-27
Well, installing the kubuntu-desktop virtual package nets you the whole Kubuntu bundle, which includes the KDE apps. Much like I would get F-Spot, gedit, Nautilus and whatnot were I to install ubuntu-desktop. :3

To change the default X cursor, do this in a terminal and pick the GNOME one (whose name I'm not sure of, but you'll probably recognize it).
```
$ sudo update-alternatives x-cursor-theme
```

By default, I believe the session started upon login will be the previously chosen session. Ergo, if you pick KDE in the menu when logging in, it will run KDE the next time you login without touching the menu. And vice versa. To change the login manager (gdm/kdm);
```
$ sudo dpkg-reconfigure kdm
```

It's possible to edit menu entries and tag them as "show only in KDE". You could manually do this for all entries via the menu editor (right-click application menu, Menu Editor). This would make it user-specific. The alternative is to (as root) edit the applications' .dekstop files in **/usr/share/applications** and add/modify the tags **OnlyShowInKDE** and **OnlyShowInGNOME** to be set to true. I think that's what the tags are called, check some of the .desktop files in there to find an example. That would make it system-wide for all users, but the change would be undone upon application update.

---

