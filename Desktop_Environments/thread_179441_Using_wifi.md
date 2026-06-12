---
title: "Using wifi"
date: 2006-05-19
forum: Desktop Environments
---

### Post by Israfel on 2006-05-19
Is there anyway I can check to see if i'm getting a wifi signal? Konqueror doesn't seem to be able to acces the internet (already tried kwifimanager). P.S. I had to use windows (blegh) to post this.

---

### Post by moephan on 2006-05-19
Open a terminal window, and type the command "iwconfig" This will tell you if you have any wifi cards set up. To see if there are any wireless connection points in range, try the command "iwlist scanning".

HTH

Cheers, Rick

---

### Post by jsvidyad on 2006-05-19
System->Administration->Networking

Ur wireless card should ne listed under network devices. Chooseit, Click On configure. choose wirless network. activate it.

---

### Post by Israfel on 2006-05-21
According to KWiFi manager, I have a signal; but Konqueror won't get on the web. Any ideas as to why this is?

---

### Post by vidak on 2006-05-21
is your non-wifi network card activated? If it is, shut it down with eg. 
sudo ifconfig eth1 down
and check your cards with ifconfig. You should see only your wifi card and "lo".

---

### Post by Israfel on 2006-05-21
The commands you gave didn't seem to work. Were there any spelling errors?

---

