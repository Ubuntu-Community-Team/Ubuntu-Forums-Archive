---
title: "Login Using Active Directory Account"
date: 2007-04-16
forum: Desktop Environments
---

### Post by kb0odu on 2007-04-16
I've done some searching (I think it's even been some decent searching on both the Ubuntu foums and with google), but I may have missed it.  If I have missed it, just send me the URL so I can fix my problems before you hit me with a clue stick.

I run Active Directory at home (and am trying to move away from it once I can get the last two Windows XP computers off my network) because I'm a SQL Server DBA (please don't hold it against me!) and need Active Directory authentication for some ttesting.  Luckily, I'm doing less of that and more MySQL / Postgres.

I'm trying to rebuild a computer (Desktop PC) and use Active Directory as my authentication source under Ubuntu.  I've got the SAMBA portion working and I can get a valid certificate from my AD Domain Controller.  However, I can't login using my domain credentials under Ubuntu (my login is KB0ODU\tim).  It works fine under OpenSuSE, so I think I've got something configured wrong.  I'm just not sure what.

I'm not even sure which config files to post at this time.  Can someone help me solve / debug this problem or send me the URL so I can start debugging it myself?

Tim

---

### Post by meadmarc on 2007-04-16
I am also very interested in this issue-

I am a middle school tech teacher who would like to begin integrating some Ubuntu machines into our Active Directory network, eventually perhaps a full lab.  I have been unable to authenticate, and will also need to mount drives for students to access their files.

If anyone has suggestions that could point me in that direction, we may have a captive audience of Ubuntu users on our hands!

Thanks!

---

### Post by kot67 [RUS] on 2007-04-17
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto?highlight=%28Winbind%29](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto?highlight=%28Winbind%29)

Look at this HOWTO, i used it and my 6.0.6LTS workstation beckme a windows 2003 domain member without any questions. Be careful about putting realm names, i found trouble when asquiring ticket like <name>@domain.com and resolved it like <name>@DOMAIN.COM

---

### Post by meadmarc on 2007-04-21
Thanks!  I'll give that a shot!

---

