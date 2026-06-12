---
title: "Kaffeine copies movies before playing..."
date: 2005-12-11
forum: General Help
---

### Post by floyd27 on 2005-12-11
Hey..
I installed kaffeine 0.7.1
xine engine, all codecs installed.
it playes the movies fine but when i open it it copies the file to "/tmp/kde-username"
It takes a few minutes for it to copy and the copied file stays there, meaning its taking up twice as much space. if i open it again another seperate copy goes to the folder....

is there a way to stop it from doing this?
thanx

---

### Post by daller on 2005-12-12
Sounds like you are running KDE3.5...

are you opening the file from "system:/home/....." ?

Changing that to "/home/<USER>" should solve it!

---

### Post by floyd27 on 2005-12-12
I think your onto something there...
I am using kde3.5 and am running our of system:/home
How would i go about changing that to what you suggested..?
thanx

---

### Post by daller on 2005-12-12
Well, haven't really tried to mess with it!

Simply made it a habbit clicking the "home" button (in the toolbar)...

You could delete the "home" button i the k-menu panel (and make "/home/<user>" the default path in konqueror)

...I'm waiting for a better implementation of the "system:/home"-feature!

Guess we have to wait for dapper...

---

### Post by floyd27 on 2005-12-12
thanx for the response.
i dont use konqueror at all and i have started just using backspace to remove the system part. There must be a way to remove it forever..

I must say ever since the upgrade to 5.10 i have been looking at other distros.. im gonna try knoppix and slakware and wait for drapper to come out. Ill give Kubuntu another try then.. I realize its not a ubuntu problem but just as i get used to ubuntu an upgrade comes out..Causing me to do everything opver again, and in this case it ends up worse.. I hope Drapper isnt as buggy... Dont worry ill be back.. :) 

ill always owe a debt to ubuntu for leading me away from window$...

---

### Post by stimpack on 2005-12-12
system: was one kioslave too far for me. Had to ditch the system menu applet(not as good in kde 3.5 anyway, no loss) and launch konq from the Konquerer applet instead, that defaults to /home/user/ instead of system:buggedtohelluser

---

### Post by ltmon on 2005-12-12
System works fine IF the ".desktop" files for each program (i.e. kaffeine.desktop) is constructed properly.

Because Kubuntu Breezy was released with KDE 3.4, the update to KDE 3.5 didn't include fixed desktop files, which is the cause of all this weird behaviour.

Basically you need to change:

```

Exec=kaffeine %U

```

to

```

Exec=kaffeine %f

```

in the .desktop file.  (I think it's under /usr/share/applications/kde).

More details are here: [http://bugs.kde.org/show_bug.cgi?id=117395](http://bugs.kde.org/show_bug.cgi?id=117395)

I've been meaning to put together a package of fixed desktop files to share around, but haven't got around to it.  But I'll think you find with this issue fixed that the system:/ ioslave in Dapper will be much better.

L.

---

### Post by vh1 on 2005-12-12
can't you also just edit the item in from kmenu to launch with "*app* %f" instead of looking for all those desktop files?

is there anywhere I can find an explaination of the arguments? so far I know there is %u, %U and %f.

---

### Post by daller on 2005-12-13
Anybody interested, This fixes OpenOffice2.0:

```

sudo perl -pi -e 's|%U|\%f|g' /usr/share/applications/ooo2-*.desktop

```

And for kaffeine:

```

sudo perl -pi -e 's|%U|\%f|g' /usr/share/applications/kde/kaffeine.desktop

```

Haven't tried it, but this should be able to fix all kde-apps:

```

sudo perl -pi -e 's|%U|\%f|g' /usr/share/applications/kde/*.desktop

```

---

### Post by ltmon on 2005-12-13
Great work Daller!

I would also suggest making sure that each .desktop file has the following as it's last line:

```

X-KDE-Protocols=http;ftp;smb; 

```

I think that this will ensure that launching non-kde apps work better when using the http, ftp and smb protocols.

L.

---

### Post by daller on 2005-12-14
WARNING: This following command is not "safe"!!!

```
sudo perl -pi -e 's|%U|\%f|g' /usr/share/applications/kde/*.desktop
```

Seems that kpdf - As one of the app - crash when applied these settings...

Please just edit each app manually.... i.e. kpdf:

```
sudo perl -pi -e 's|%U|\%f|g' /usr/share/applications/kde/kpdf.desktop
```

Thanks!!!

---

