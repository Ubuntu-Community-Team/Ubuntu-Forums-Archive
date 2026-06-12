---
title: "kopete msn login problem"
date: 2005-11-28
forum: Desktop Environments
---

### Post by seppo on 2005-11-28
Hi Folks,

after a year of ubuntu experience, i decided to give kubuntu a try. Currently I'm having problems connecting to msn via kopete (it can't connect)

software:
Kubuntu 5.10
KDE 3.4.3
Kopete 0.10.4
msn server: messenger.hotmail.com:1863

I verified that it isn't related to my internet connection or M$: Miranda on Windows has no issues.

Ofcourse i googled first ad i noticed much problems with older versions of kopete. Version 0.10.x should solve MSN related problems.

Anybody got a clue?

---

### Post by loupy on 2005-11-28
I know this doesn't answer your question - but maybe you want to try Gaim in KDE.  I never was able to use Kopete because it doesn't support lotus sametime.  The only issue I had with Gaim under KDE was changing the sound server from automatic to arts in order to hear sound properly.

---

### Post by seppo on 2005-11-28
[QUOTE=loupy]I know this doesn't answer your question - but maybe you want to try Gaim in KDE.  I never was able to use Kopete because it doesn't support lotus sametime.  The only issue I had with Gaim under KDE was changing the sound server from automatic to arts in order to hear sound properly.[/QUOTE]

Thanks Loupy, i know gaim pretty well, but i really need Kopete working. I really need the tight integration with KDE components.

ICQ works perfectly inside kopete, but i have to change friends if I'll stick to ICQ only ;)

---

### Post by loupy on 2005-11-28
I just tried it and it worked for me.  I assume you have kopete 0.10.4 - in the configuration though I do not have override system defaults.  How are you setup?

---

### Post by seppo on 2005-11-29
[QUOTE=loupy]I just tried it and it worked for me.  I assume you have kopete 0.10.4 - in the configuration though I do not have override system defaults.  How are you setup?[/QUOTE]

Kopete 0.10.4 ( 4:3.4.3-0ubuntu1) with system defaults. Breezy is running with main, multiverse and universe repositories.

This is strange! Are there any additional NAT rules neccessary for Kopete in comparison with other MSN clients? I've tried Miranda and Trillian on another windows pc in the same network (ADSL behind router) and that worked.

---

### Post by seppo on 2005-11-29
Ok update to make sure it isn't network related: I installed centericq on the same desktop and it can connect with MSN without problems. So it is a Kopete related problem.

If i run Kopete form the command line I get:

kopete (msn): WARNING: [void MSNSocket::slotSocketError(int)] Error: 17 (remote host closed connection)

Ok update:

I updated to KDE 3.5.0 with Kopete 0.11. Removed ~/.kde/share/apps/kopete and added my msn account again. Now i get endless prompts for my MSN account saying I've entered a wrong password (which obviously isn't the case).

---

### Post by seppo on 2005-11-30
Ok another update:

Today i did a complete fresh install on another piece of hardware. 

Again Kubuntu 5.10 with KDE 3.4.3, Kopete 0.10.4. With this install I'm also unable to connect to MSN with Kopete. I configured my MSN account, settings are at system default. I really spend a lot of time looking at the KDE forum, but their statement is, that this so called bug I'm facing, is already fixed since version 0.10.1.  :( 

I've got no clue what is wrong with my configurations. Can anybody post a reply if he/ she can connect to MSN with Kopete 0.10.4 provided in Kubuntu 5.10 (a.k.a Breezy)?  Can you also point out what they have changed to get it working?

Thanks in advance :)

---

### Post by GeneralZod on 2005-11-30
Hi Seppo,

I don't have the answer to your question, but I'm running the stock Kopete that came with Kubuntu 5.10 on my desktop and laptop and can connect to MSN on both with no problems, although I inherited my configuration from 5.04 so it's possible I made some changes ages ago and have forgotten all about them :)

---

### Post by seppo on 2005-11-30
[QUOTE=GeneralZod]Hi Seppo,

I don't have the answer to your question, but I'm running the stock Kopete that came with Kubuntu 5.10 on my desktop and laptop and can connect to MSN on both with no problems, although I inherited my configuration from 5.04 so it's possible I made some changes ages ago and have forgotten all about them :)[/QUOTE]

Thanks GeneralZod. I really appreciate that. So it must be my configuration!  Strange that with 2 fresh installs I've got the same problem. I hope somebody else can give me a clue.

---

### Post by f1dave on 2005-11-30
I too have a working kopete in breezy, straight-out-of-the-box so to speak. I know it sounds silly, and that you've probably tested this already, but you may want to double check your username and password are correct. Also, another idea may be to create a new msn account and see if kopete can connect to that.

---

### Post by seppo on 2005-12-01
[QUOTE=f1dave]I too have a working kopete in breezy, straight-out-of-the-box so to speak. I know it sounds silly, and that you've probably tested this already, but you may want to double check your username and password are correct. Also, another idea may be to create a new msn account and see if kopete can connect to that.[/QUOTE]

Hi dave, Username and password are correct. I can connect with gaim and centericq within the same installation. I just created a new passport and I am also unable to connect with this account in Kopete.

I'm lost :( 

Could anybody provide me his/her kopete config file (~.kde/share/config/kopeterc) so I can compare it with mine?

Thanks in advance

---

### Post by daller on 2005-12-14
I have a similar problem, I get logged off MSN every minute or so...

Are there any differences on when the account is created? (the comment about creating a new)

---

### Post by daller on 2005-12-14
[QUOTE=seppo]Ok update to make sure it isn't network related: I installed centericq on the same desktop and it can connect with MSN without problems. So it is a Kopete related problem.

If i run Kopete form the command line I get:

kopete (msn): WARNING: [void MSNSocket::slotSocketError(int)] Error: 17 (remote host closed connection)

Ok update:

I updated to KDE 3.5.0 with Kopete 0.11. Removed ~/.kde/share/apps/kopete and added my msn account again. Now i get endless prompts for my MSN account saying I've entered a wrong password (which obviously isn't the case).[/QUOTE]

Oki, I get the exact same error: (in danish)

kopete (msn): WARNING: [void MSNSocket::slotSocketError(int)] Error: 17 (ekstern vært lukkede for forbindelsen)

Where are you running msn from? (I only have this issue in school!)

---

### Post by Rackerz on 2005-12-14
The Kopete shipped with breezy, (KDE 3.4.3) has issues apprently. Upgrade to KDE 3.5 it should fix the problems.

---

### Post by greatshape on 2005-12-15
[QUOTE=Rackerz]The Kopete shipped with breezy, (KDE 3.4.3) has issues apprently. Upgrade to KDE 3.5 it should fix the problems.[/QUOTE]

No problems here with breezy, KDE 3.4.3, kopete 0.10.4 
Though i didn't do a fresh breezy install. I've upgraded from hoary when breezy released, but this shouldn't make any difference.

Regards,
Steve

---

### Post by Jagunço on 2005-12-15
I don´t know if this can put some light over the problem, but I had a similar issue some months ago. I was using MDK 10.1 then, and suddenly Kopete stopped to work. Gaim worked just fine in the same machine, but I wasn´t able to connect to MSN with Kopete anymore.
Recently I changed to Kubuntu 5.10, and Kopete is working fine since.
Sorry for the poor english.

---

### Post by daller on 2005-12-15
Having Kopete 0.11 (Kubuntu 5.10) - Still no luck!

...I'm not much of a MSN-guy, so it doesn't bug me!

I'm supporting people, and they want to contact me (not vise versa) - So i'll give them my Jabber-account - Problem solved :D (I'm not dependant of any people with MSN-accounts)

---

