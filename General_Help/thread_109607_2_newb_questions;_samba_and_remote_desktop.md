---
title: "2 newb questions; samba and remote desktop"
date: 2005-12-29
forum: General Help
---

### Post by ERIC H on 2005-12-29
firstly, i am pretty newbie to linux in general and using ubuntu for the first time (and loving it) though i've dabbled in linux for the last couple years now and again. i just installed, about 8 hours ago, the latest release and am up to date. i have 2 questions and thought i would consolidate them to one thread.

number 1. 

using tightvnc on my XP machine to view ubuntu machine (p3 1.26ghz w/512MB ram). works ok but i've noticed that no matter the compression i use at least 20% load is put on the p3. realvnc is worse, nearly 60% load. even just opening folders pushes it to full load. i've run win2000 and XP on the p3 and never had this issue with any vnc server. is this normal? i don't even know where to begin to try and fix it if it isn't.

number 2.

using the ubuntuguide to try and setup samba. everything seemed to go ok. testparm spit back all that i had put in smb.conf for the share so i restart samba daemon. XP machine just gives me errors saying network place unavailable due to permissions blah blah blah and when i do testparm again i'm getting this:

[img]http://img399.imageshack.us/img399/955/term9ev.png[/img]

though this is in smb.conf:

[img]http://img399.imageshack.us/img399/436/smbconf0gf.png[/img]

looks like it's obviously not available to the windows network but no matter how many times i restart samba or reboot it doesn't change.

any help is much appreciated. [-o<

---

### Post by ERIC H on 2005-12-29
bump*

any help?

---

### Post by KnottyMan on 2005-12-29
VNC, no idea sorry.

Samba:

What do you want to accomplist with this share?  Depending on what you want, certain options need to be set.  I looks like you want anybody to be able to get to those files, but yet you have guest ok = no...

I use the users group instead of nogroup.  Also, you need an account on the samba machine for your XP user.  You also need a smbpasswd entry for that user (using USER auth style - there are other types [active directory])

Also, that path is valid?  Check file permissions on the directory.  Users need rx on the folder, r on the files, maybe x.

---

### Post by stevea1210 on 2005-12-29
As far as VNC goes, I have experimented with several flavors, and found tight to be the best.  That said, it isn't always great.  Disableing wallpaper can help with the speed.

You may want to look into freenx, search the forums, there are lots of threads raving about it.  I haven't tried it yet, but am getting fed up with vnc, and may do so this weekend.

---

### Post by ERIC H on 2005-12-30
[QUOTE=KnottyMan]VNC, no idea sorry.

Samba:

What do you want to accomplist with this share?  Depending on what you want, certain options need to be set.  I looks like you want anybody to be able to get to those files, but yet you have guest ok = no...

I use the users group instead of nogroup.  Also, you need an account on the samba machine for your XP user.  You also need a smbpasswd entry for that user (using USER auth style - there are other types [active directory])

Also, that path is valid?  Check file permissions on the directory.  Users need rx on the folder, r on the files, maybe x.[/QUOTE]


i basically only want to full access while i install q3 so i can update configs and whatnot from windows, add maps, etc. untill i get the server setup. this is essentially to replace vnc if it's not going to work how i want it to.

share username and pass have both been set and are the same that i use in windows. thing is, i created the username and pass first, and then smb.conf, but it still didn't work. and when i restarted samba daemon, there was that bit about the guest ok = no when i did testparm though it wasn't in smb.conf. i only then put that in smb.conf when i saw that it was showing up in terminal.

i saved a backup of smb.conf before i started messing around, so i guess i'll start over and recreate smb username and password, then the appropriate info for the share. should i remove anything i've put in as a share through system>administration>shared folders? i tried doing that first before editing stuff in samba...

hope any of that made sense :)

---

### Post by ERIC H on 2005-12-30
[QUOTE=stevea1210]As far as VNC goes, I have experimented with several flavors, and found tight to be the best.  That said, it isn't always great.  Disableing wallpaper can help with the speed.

You may want to look into freenx, search the forums, there are lots of threads raving about it.  I haven't tried it yet, but am getting fed up with vnc, and may do so this weekend.[/QUOTE]


i've tried the fastest compression, least color depth etc. and it still slows it down and taxes the cpu. i have another monitor sitting here on my desk so i may just bite the bullet and set everything i need to up the old fashioned way and then use vnc for minor things.

and thx, i'll look into freenx first.

edit: one thing i'm just noticing, i have system monitor open and when i'm viewing usage stats, it shows the cpu at 20% load. if i then minimize and just let it sit there maybe 10 seconds, it will go down to 2-4%, which is what i would expect it to be while running vnc. but, browsing directories totally lags it out still.

---

