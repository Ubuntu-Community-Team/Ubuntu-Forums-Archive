---
title: "Amarok Playing Songs"
date: 2006-05-28
forum: Desktop Environments
---

### Post by Mau on 2006-05-28
After I upgraded to Dapper today, Amarok no longer plays my songs.  Instead, it just goes through the play-list really fast.  ](*,)  Is there any way to fix this?

---

### Post by CitizenKane on 2006-05-28
I don't know a surefire way.  I just kind of beat amarok until it worked (aka adding packages).  I would make sure that you have w32codecs installed.  Additionally, try the following in Konsole.

```

sudo apt-get update
sudo apt-get install amarok-arts amarok-engines amarok-xine libmad0 libxine-extracodecs

```

I will try to narrow it down as it seems a number of people are having this problem.

---

### Post by Mau on 2006-05-28
Finally, a bug that is common!  I seem to get the rare ones.  

I will try installing a bunch of packages.  I have all the amarok-* ones.

---

### Post by croak77 on 2006-05-28
If you are using the xine engine, then you need libxine-extracodecs.

---

### Post by vidak on 2006-05-29
Try other engines too... Here xine engine works, but this was not the default one after install...

---

### Post by der_joachim on 2006-05-29
[QUOTE=Mau]After I upgraded to Dapper today, Amarok no longer plays my songs.  Instead, it just goes through the play-list really fast.  ](*,)  Is there any way to fix this?[/QUOTE]

The 1.3.9 version in the standard Dapper repo is um... flawed.I had lots of crashes and suddenly it stopped updating my collection. Upgrading to Amarok 1.4 did fix a lot of things. Although I had to rebuild my collection, the crashes have disappeared altogether. 

Read [this announcement]("http://kubuntu.org/announcements/amarok-1.4.php") for instructions how to upgrade.

---

### Post by Mau on 2006-05-29
I tried updating to the latest Amarok (Fast Forward), and I could play the welcome clip just fine.  However, none of my music is playing--it just "fast forwards" to the end.

---

### Post by Mau on 2006-05-29
Okay, I just found out that libxine-extracodecs is NOT installed.  When I apt-get it, it says that it's missing, but found.  This seems to be the problem.  What source do I need to add to get this working?

---

### Post by Jucato on 2006-05-29
libxine-extracodecs is in the multiverse repository, AFAIK.

---

### Post by Mau on 2006-05-29
Got it to work.  I generated a new sources list from here:[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) .  I then installed libxine-extracodecs.  I had to re-install Amarok, but it works now.  Painful!

---

### Post by asimon on 2006-06-01
[QUOTE=Mau]Painful![/QUOTE]
Absolutely. The plan is that amaroK 2 will handle these situations much more gracefully:

From [dot.kde.org](http://dot.kde.org/1148805012/): "Ian Monroe and Max Howell have been working on better error messages for the users if there is no mp3 support in the distribution they use. The distribution has to provide a script for amaroK so it can offer the user to automatically install the nessecary codecs. Cooperation has already been promised by Jonathan Riddell from Kubuntu."

---

