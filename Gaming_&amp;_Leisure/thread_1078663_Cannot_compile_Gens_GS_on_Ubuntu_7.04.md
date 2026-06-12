---
title: "Cannot compile Gens GS on Ubuntu 7.04"
date: 2009-02-23
forum: Gaming &amp; Leisure
---

### Post by Fisher on 2009-02-23
Hi, I cannot compile Gens GS, Milestone 6 on Ubuntu 7.04, I got this error:
ui/gtk/gens/gens_window_callbacks.cpp:127: error: ‘g_uri_unescape_string’ was not declared in this scope
Installing from the deb package gives a Glibc error, I think the only way is to compile with this system.
Upgrade to a newer Ubuntu is not an option, since I am using a multiseat pc and the configuration just doesn't work with newer versions I don't know why so, I think I'm stuck with 7.04, but the machine is running fine :-)

---

### Post by Fisher on 2009-04-08
Don't anyone have any idea??

---

### Post by wingnux on 2009-04-08
Why don't you download the deb instead?? It's so much easier ;)

---

### Post by GerbilSoft on 2009-04-10
g_uri_unescape_string() was added in GLib 2.16. Ubuntu 7.04 doesn't have GLib 2.16, so you get that error.

I added an internal copy of this function to the git version of Gens/GS. The two patches are available on my gitweb server:

ui/gtk/gtk-uri.c: Imported the g_uri_unescape_string() function from glib-2.18.4.
[http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commit;h=fcd92e5711929586796f8905370b3afe525276bd](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commit;h=fcd92e5711929586796f8905370b3afe525276bd)

[GTK+] gens_window_callbacks.cpp: Use gens_g_uri_unescape_string().
[http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commit;h=f8fb428dc77e4580e86914e97062eac345a1ead5](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commit;h=f8fb428dc77e4580e86914e97062eac345a1ead5)

---

### Post by Fisher on 2009-04-14
Ok, I installed it from the .deb, get a weird glibc++ problem, but solved doing the follow:
1- Copyed libstdc++.so.6.0.9 from Ubuntu 8.04 (/usr/lib);
2- Created a symlink, named libstdc++.so.z;
3- Edited the gens executable (/usr/bin/gens), and changed the string that was libstdc++.so.6 to libstdc++.so.z.

Seems to work fine, need a bit more of testing.
I would love to upgrade to 8.10, or even the newest 9 series, but I'm using a multiseat machine wich I could get Opengl working fine on the Nvidia head, and I could not do the same on the newer versions.

Many thanks for all!! ;)

---

### Post by markcream on 2009-04-15
Why not?
:)

[right][[color=#EEEEEE]_ What Is The Best Stretch Mark Cream_[/color]](http://ezinearticles.com/?What-is-the-Best-Stretch-Mark-Removal-Cream?&id=1804667)[/right]

---

### Post by Fisher on 2009-04-15
It is a machine that is serving as two.
To get the video acceleration activated, a thing I could not get with Xephir or similar solutions. I created 2 individual Layouts on Xorg.conf, then, in gdm.conf I started one, then the other.
In the new versions this simply don't work. And I did not have enough time or patience to find out why.
It's cool because you save energy!! And you don't need to download anything else, just change config files.

---

