---
title: "&quot;Disks&quot; disappeared in the System/Admin"
date: 2007-03-09
forum: Desktop Environments
---

### Post by medya on 2007-03-09
Hi , I upgraded my Dapper , to Edgy , now I wanted to mount one of my windows drives... I noticed there is no more "Disks" in the "system / adminstrator"

what to do ?:( 

P.S : after upgrading I installed NTFS configuration tool.

---

### Post by PriceChild on 2007-03-09
I got annoyed at that disappearing too :)

You could use gparted... or "mount /dev/foo /media/foo"

---

### Post by medya on 2007-03-09
you mean there is no way to fix it ? you know what I want to mount one of my partitions but I dont know which one it was... I can find out just by looking at the table in the "Disks" ... so how can we restore it?

---

### Post by PriceChild on 2007-03-09
I can't personally remember the name for that gui... hopefully someone else might be able to help...

---

### Post by mmmichael on 2007-03-09
System>Administration>Gnome Partition Editor will bring up gparted, which gives some information on your partitions, but I don't know if it gives everything you're looking for.

---

### Post by tagginannie on 2007-03-10
> **PriceChild said:**
> I can't personally remember the name for that gui... hopefully someone else might be able to help...

Do you mean the Disk Monitor applet? Ubuntu removed it 
not because off support issues Gnome still supports it. It is 
because they don't know how to get it working with hal, 
Launch pad _[[disk-admin] need to be rewritten with the new API and]("https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/61728")_
_[ using hal]("https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/61728")_ I searched google could not find the new tool but I did find
the Original one that can be used on newer versions of Gnome
_[Original]("http://www.gnomefiles.org/app.php/Original_Disk_Mount_Applet")[Disk Mount]("http://www.gnomefiles.org/app.php/Original_Disk_Mount_Applet")[Tool]("http://www.gnomefiles.org/app.php/Original_Disk_Mount_Applet")_ I Don't know how well it will work for you
cause I use the better desktop, KDE :grin:

---

### Post by Carl H on 2007-03-11
System > Admin > Disks runs "disks-admin" on 6.06, which isn't available for 6.10. 

A lot more detail about this can be found in [this thread]("http://ubuntuforums.org/showthread.php?t=260317")

---

### Post by tagginannie on 2007-03-13
> **Carl H said:**
> System > Admin > Disks runs "disks-admin" on 6.06, which isn't available for 6.10. 

A lot more detail about this can be found in [this thread]("http://ubuntuforums.org/showthread.php?t=260317")

That thread is old and full of a lot of misinformation. Gnome did not
removed it, it was Ubuntu who did because of API and HAL
issues. Gnome Still includes that feature and includes a lot of new
stuff but it wont be in any new releases. If you want it you will
have to download the source files from_ [http://www.gnome.org]("http://www.gnome.org/")_
and compile and install it or you can take the easy out _[Pure Gnome]("http://www.psychocats.net/ubuntu/puregnome")_

---

