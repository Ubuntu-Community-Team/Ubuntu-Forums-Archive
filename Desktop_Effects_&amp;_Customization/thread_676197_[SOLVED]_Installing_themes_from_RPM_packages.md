---
title: "[SOLVED] Installing themes from RPM packages?"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by Sain on 2008-01-23
I've downloaded some Gnome and KDE themes, however they are packaged in rpm (they're made for Mandriva). I tried to install them with alien, but no luck. 

Here's the output:

```

warning: ia_ora-gnome-1.0.16-1mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3 


chown: changing ownership of `ia_ora-gnome-1.0.16//usr/share/doc/ia_ora-gnome': Operation not permitted
failed chowning /usr/share/doc/ia_ora-gnome to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 246, <GETPERMS> line 1.

```

It's Mandriva's default "ia ora" theme. I like it because there is both Gnome and KDE version, so it gives unified look of application and desktop no matter if they use GTK or QT...

Is there a way to install it? I attached an archive with themes...

---

### Post by Sain on 2008-01-28
Bump. Should I post this in other subforum?

---

### Post by Tenken on 2008-01-28
You could try a program called [Alien]("http://packages.ubuntu.com/gutsy/admin/alien"), to install rpm files. I've never used it but from my understanding it doesn't work with a *.rpm files, but it's worth a shot.

---

### Post by Sain on 2008-01-29
I *have* tried to install them with Alien but had no luck! 
Thats why I asked this question in the first place, maybe someone who knows about Alien and its features more than I do can install these themes....

---

### Post by amo-ej1 on 2008-01-29
It gives you a permission denied, just a wild guess here but did you put sudo in front of it ?

---

### Post by jryprt on 2008-01-29
Code this one at a time```
sudo su
apt-get install rpm
apt-get install alien
apt-get install libpng3
apt-get install libqt3-mt
sudo apt-get install fakeroot
exit
```
Download the zip to your desktop , right click it & extract it to your desktop , than open the extracted file , this is the codes for the 1st one 
Then ```
cd Desktop
```
```
fakeroot alien -d ia_ora-gnome-1.0.16-1mdv2008.0.i586.rpm

```
```
 sudo dpkg -i ia-ora-gnome_1.0.16-2_i386.deb
```
Thats how to turn an .rpm to .deb  , I did the 1st one but I do not know where it is ?
After you do the fakeroot alien -d ia_ora-gnome-1.0.16-1mdv2008.0.i586.rpm  look at your desktop it will give you the .deb name (ia-ora-gnome_1.0.16-2_i386.deb)

---

### Post by Sain on 2008-02-02
I got it to install using instructions above. 

However it seems that Ia Ora does not work well with Ubuntu. Only thing that works is Metacity border, GTK theme itself does not, nor does KDE theme. This is probably due to different versions of GTK and Qt libraries Ia Ora uses (at least this version I have).

---

