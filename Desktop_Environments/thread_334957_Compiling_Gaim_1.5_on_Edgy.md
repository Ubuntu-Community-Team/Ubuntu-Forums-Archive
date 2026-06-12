---
title: "Compiling Gaim 1.5 on Edgy"
date: 2007-01-09
forum: Desktop Environments
---

### Post by ktulu1115 on 2007-01-09
This is probably a shot in the dark, but I'm wondering if anyone has experience compiling Gaim 1.5 on Edgy...  there seem to be a problem in the Makefile when linking:

```
/bin/bash ../libtool --silent --tag=CC --mode=link gcc  -g -O2 -Wall -g3   -o gaim -export-dynamic account.o accountopt.o blist.o buddyicon.o cmds.o connection.o conversation.o core.o debug.o eventloop.o ft.o imgstore.o log.o md5.o network.o notify.o plugin.o pluginpref.o pounce.o prefix.o prefs.o privacy.o proxy.o prpl.o request.o roomlist.o server.o sha.o signals.o status.o stringref.o sound.o sslconn.o util.o value.o xmlnode.o away.o dnd-hints.o gaim-disclosure.o gtkaccount.o gtkcellrendererprogress.o gtkblist.o gtkconn.o gtkconv.o gtkdebug.o gtkdialogs.o gtkeventloop.o gtkft.o gtkimhtml.o gtkimhtmltoolbar.o gtklog.o gtknotify.o gtkplugin.o gtkpluginpref.o gtkprefs.o gtkprivacy.o gtkpounce.o gtkrequest.o gtkroomlist.o gtksound.o gtksourceiter.o gtkutils.o idle.o main.o session.o stock.o themes.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0      -LNONE -lSM -lICE    -lnsl 
../libtool: line 1799: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
make[3]: *** [gaim] Error 1
make[3]: Leaving directory `/home/ktulu/gaim-1.5.0/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ktulu/gaim-1.5.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ktulu/gaim-1.5.0'
make: *** [all] Error 2
```

I want v1.5 because all later versions do not have the "Queue new messages when away" option in Preferences....  I have no idea why it was removed, I think it was a dumb idea to be honest but can't seem to find a better replacement IM client.

---

### Post by bruenig on 2007-01-09
What do you mean by queue, what does that actually do?

---

### Post by ktulu1115 on 2007-01-09
> **bruenig said:**
> What do you mean by queue, what does that actually do?

What is does is list any messages you have while away in a little window.  With that setting disabled on Gaim 1.5, the messages would just appear normally as if you weren't away.  With v2.0 beta 1 and newer, the only notification you have messages while away is it changes the status icon of the user in your buddy list - there's no way to actually view the message until you return from away.

I like to leave an away message up most of the time but still chat with other users and see messages they might have sent me which were "queued" up while away.  It's pretty much the default behavior that AOL's actual AIM client uses...  or at least used to last time I ran it (many many moons ago).

---

### Post by bruenig on 2007-01-09
Well here is a 1.5 deb, seems easier.
[http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.5.0-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.5.0-1ubuntu3_i386.deb)

You might also need the gaim-data package, not positive
[http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim-data_1.5.0-1ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim-data_1.5.0-1ubuntu3_all.deb)

But as for the queue, can't you just select the 'hide new messages when away' feature or is that different.

---

### Post by ktulu1115 on 2007-01-09
> **bruenig said:**
> Well here is a 1.5 deb, seems easier.
[http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.5.0-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.5.0-1ubuntu3_i386.deb)

You might also need the gaim-data package, not positive
[http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim-data_1.5.0-1ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim-data_1.5.0-1ubuntu3_all.deb)

But as for the queue, can't you just select the 'hide new messages when away' feature or is that different.

Thank for the links, but unfortunately it won't install - depends on libgnutls11...  try installing that, then it depends on other libraries, etc...   basically a dependency hell.

Hide new messages when away is only 1/2 the functionality I want - when you enable that, it does indeed hide the messages - but the problem is it hides them completely - you can't read/view or even be able to tell in anyway whatsoever how many you have and whom they are from unless you return from away.  The old version of Gaim (1.5) had a nice little dialog box that listed all the messages you had queued when away.

---

### Post by bruenig on 2007-01-09
I would assume doing a
```
sudo apt-get build-dep gaim
```
should get some if not all the necessary dependencies for this, especially since you are going back instead of forward.

---

