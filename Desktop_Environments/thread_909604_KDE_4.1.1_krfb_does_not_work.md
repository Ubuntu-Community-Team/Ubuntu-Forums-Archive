---
title: "KDE 4.1.1 krfb does not work"
date: 2008-09-03
forum: Desktop Environments
---

### Post by warhammerkid on 2008-09-03
After starting KDE 4 krfb to allow VNC connections, I connect locally to the computer using krdc and I see an image of the screen at the instant of connection, but it never changes. Repeated VNC connections display the exact same image. Mouse interaction seems like it still works, but the display does not get updated. What am I doing wrong to experience this, because I haven't found any other reports of krfb issues in KDE 4?

---

### Post by cypher35 on 2008-10-04
I just wanted to say that I've got the exact same problem...  has anyone else gotten kfrb working correctly in kde4?

---

### Post by toucan on 2008-11-22
Yes, I have exactly the same problem. Connection is OK and mouse control is OK, but the image is only updated once on the initial connection and then never refreshed. I've tried a couple of different clients... the problem seems to be the server (KRFB)

Anybody managed to get KDE Desktop Sharing working under KDE 4 ?

Steve

---

### Post by kkaal on 2009-01-17
I have exactly the same problem. Kubuntu 8.10. I am trying to connect to the desktop from Win XP and Vista using the UltraVNC client.

Do we need to file a bug? How would we do that?

---

### Post by rclark33 on 2009-02-25
I'm running Jaunty with the KDE nightly builds, and have found that krfb does not work. The local KDE session works fine, but connecting remotely with VNC is clearly broken.

I started with a Gnome based Ubuntu Jaunty system, and added the optional KDE nightly packages. When running Gnome there are no issues connecting to a Gnome session from either WindowsXP, Windows Vista, or Ubuntu Intrepid or Jaunty.

When the connection to the remote machine is established, I see the KDE desktop, but the colors are random. In addition the applications are also shifted. The mouse appears to track, but it does not make sense to click/select on the distorted display.

---

### Post by Fungyo on 2009-03-02
same problem here. found this bug report: [https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/301448]("https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/301448")

---

### Post by anachreon_ on 2009-04-07
It used to work for me (in Fall 2008), but now that I am using KDE 4.2.x, it no longer works for me.  Very frustrating, I hope it gets fixed.  Are there any other KDE 4.x remote desktop solutions?

---

### Post by poet_imp on 2009-04-30
This post is #1 in google for "krfb not working Jaunty". I thought I would bump it and see if anybody has found a solution yet.

---

### Post by dale456654 on 2009-10-04
No solution in 4 months still? I have the same problem, i really really want this to work.

---

### Post by ciuci on 2009-10-30
same problem here, kubuntu karmic, and i also tried it in jaunty with the same results.... the destkop sharing server clearly does not work... will nobody fix this? is there not any workaround?

---

### Post by Jelloir on 2010-01-30
> **ciuci said:**
> same problem here, kubuntu karmic, and i also tried it in jaunty with the same results.... the destkop sharing server clearly does not work... will nobody fix this? is there not any workaround?

Please revisit the bug report for a possible workaround...

---

