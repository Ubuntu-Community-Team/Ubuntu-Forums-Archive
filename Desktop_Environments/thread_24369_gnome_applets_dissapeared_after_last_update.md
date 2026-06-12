---
title: "gnome applets dissapeared after last update"
date: 2005-04-06
forum: Desktop Environments
---

### Post by occy8 on 2005-04-06
Hi,
after yesterdays update the wastebasket dissappeared from the pane and also from 
the add to panel list

at the end of the update I got this error message
E: gnome-applets-data:  subprocess post-installation script returned error exit status 134

after sign on I get these messages
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
The panel encountered a problem while loading "OAFIID:GNOME_MultiLoadApplet".
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

What can I do??
I didthe latest updates just now but its still the same

---

### Post by jeremy on 2005-04-06
I did the update with no errors, but my Pilot Applet has dissapeared, it is still there and still works, but is invisible.

---

### Post by dejitarob on 2005-04-07
Yea I'm still trying to figure out how to get my system monitor applet back. A few days ago it just disappeared after updates. Adding another one does not work.

Ok, ran a 'apt-get install gnome-applets-data' to reinstall it. If that doesn't work try doing it through synaptic.

---

### Post by occy8 on 2005-04-08
I did 'apt-get install gnome-applets-data'
but this is what happens any idea what I can do next?

(process:8370): GConf-CRITICAL **: gconf_schema_get_type: assertion `schema != N ULL' failed

** ERROR **: file mc-install-default-macros.c: line 84 (install_default_macros_l ist): assertion failed: (gconf_schema_get_type (schema) == GCONF_VALUE_LIST)
aborting...
/var/lib/dpkg/info/gnome-applets-data.postinst: line 31:  8370 Aborted        HOME=/root GCONF_CONFIG_SOURCE=`gconftool-2 --get-default-source` /usr/li b/gnome-applets/mc-install-default-macros >/dev/null
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 gnome-applets-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by occy8 on 2005-04-08
a gentle attention seeking bump

---

### Post by iminj on 2005-04-10
Hi:

I have a similar problem ... so you're NOT alone.

Following a fresh install of hoary, synaptic reported that my ubuntu-desktop was broken. I reinstalled this package from synaptic, and now I have 2 of the 3 OAFIID:GNOME errors that you had:

MixerApplet
Panel_TrashApplet

I haven't yet tried apt-get install gnome-applets-data ... 

I posted this in the hoary installation forum and haven't received a reply, so I assume this isn't a common issue. I'm thinking about downloading the .iso again and burning a new installation CD. 

If you've found another solution, please post it here. Thanks!

-iminj


-iminj

---

### Post by occy8 on 2005-04-10
good to here I'm not alone :grin: 
I get a similar message to this everytime I install something. Just the process number changes. and at the end of the install synaptic locks up.


> (process:8370): GConf-CRITICAL **: gconf_schema_get_type: assertion `schema != N ULL' failed

** ERROR **: file mc-install-default-macros.c: line 84 (install_default_macros_l ist): assertion failed: (gconf_schema_get_type (schema) == GCONF_VALUE_LIST)
aborting...
/var/lib/dpkg/info/gnome-applets-data.postinst: line 31: 8370 Aborted HOME=/root GCONF_CONFIG_SOURCE=`gconftool-2 --get-default-source` /usr/li b/gnome-applets/mc-install-default-macros >/dev/null
dpkg: error processing gnome-applets-data (--configure):
subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
gnome-applets-data
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by occy8 on 2005-04-11
Bump

---

### Post by iminj on 2005-04-11
I gave up on the dist-upgrade approach, as I was going nowhere. Instead, I installed warty from it's orginal CD. Then from a fresh warty, I upgraded to hoary. It booted without the GNOME, desktop, and kernel problems that thwarted me before.

I described the process in the hoary installation forum on April 11. It worked for me ... I can't assure you that it will also work for you.

-iminj

---

### Post by occy8 on 2005-04-11
I don't really want to reinstall everything, unless it is necessary.
It looks to me like a corrupted config file, or something like it. I'm sure someone can help me to work out what the problem is.

---

### Post by stoneguy on 2005-04-11
[QUOTE=iminj]I gave up on the dist-upgrade approach, as I was going nowhere. Instead, I installed warty from it's orginal CD. Then from a fresh warty, I upgraded to hoary. It booted without the GNOME, desktop, and kernel problems that thwarted me before.
-iminj[/QUOTE]

Ummm, why didn't you just start anew with the hoary CD?

---

### Post by iminj on 2005-04-12
[QUOTE=stoneguy]Ummm, why didn't you just start anew with the hoary CD?[/QUOTE]
 Because installing from a hoary CD was problematic for me - ubuntu-desktop was broken, assorted x.org server failures, and gnome applets failing to load. I tried several times ... and the only method that worked for me was going back to a clean warty and doing a dist-upgrade from there.

---

### Post by abovett on 2005-04-12
Sounds like a dodgy CD or something to me. I've not had a problem when doing a test install with the released Hoary ISO - and you _should_ end up with the same thing (barring extra packages you've installed) when doing apt-get dist-upgrade.

One thing you might try as a trouble-shooting aid: Create a new user and see if the problems occur when logging in as that user. If they don't, it's something in your personal configuration that's messed up rather than the system itself. That could be in your home directory, or maybe something in /var or /tmp.

HTH

Andy B

---

### Post by occy8 on 2005-04-12
Its not a CD problem with my installation because it happened after a Synaptec update. The problem exists as well in root user and in a new user I just created to try.

Hmmm 170 views and no ideas??? Cmon guys!!!

---

### Post by occy8 on 2005-04-13
Help !!!!!

---

