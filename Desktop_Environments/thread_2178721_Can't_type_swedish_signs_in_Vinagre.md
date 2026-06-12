---
title: "Can't type swedish signs in Vinagre"
date: 2013-10-04
forum: Desktop Environments
---

### Post by Azyx on 2013-10-04
Hi. Use 12.04LTS on both server and client.

I suddenly get problem to read swedish signs (**åä****ö**) from [COLOR=#ffa500]**Clementine**[/COLOR] music player.
From [COLOR=#ff8c00]**Clementine**[/COLOR] folders browser, folders with **åä****ö** looked like a file without **åäö**. The music-folders are on a remote machine using samba.

I have changed my Desktop client language support from Swedish to English and when I have installed applications, they have said that Locale have being missed, or something. So I get to:
 
'System settings--> Language support --> Language: And there are English and English (USA)

and under 'Regional formats I choose 'Svenska (Swedish)'

My 'samba share' works both to read and write **åä****ö**, and also in [COLOR=#ffa500]**Clementine**[/COLOR] **:)**

BUT with '[COLOR=#800080]**Vinage**[/COLOR] - Desk top Viewer' I can not type **åä****ö** on a remote Machinne, also with Ubuntu 12.04LTS. I can read **åäö**, but when I try to type **åä****ö** the keystroke are dead.

I have the same problem with SSVNC as a client. But I have not change the[COLOR=#800080] **Vino-server **[/COLOR]on the remote machine

Cheers

[COLOR=#ee82ee]***I was really tired when I woke up last night, so my English was unreadable. Hope that is simpler now.***[/COLOR]

---

### Post by Azyx on 2013-10-05
I also made the same steps on the my remote desktops, with [COLOR=#800080]**Vino-server**[/COLOR],  Language support English for menu and application and pressed 'System wide' and under Regional Formats Svenska (Sverige) and Apply system-wide. And still the server do not receives **åäö**

Cheers

Edit.

I tested to logout and login to Gnome classic (No effect), Gnome Classic, Unity 2D (on the Remote machine with Vino-server) and it could receive **åäö** :)
After that also Unity 3D could receive **åäö** .) BUT the processor get up to near 100% use, when I connect with vinagre, with the results of huge lag, and impossible to use :(

Very strange!!!!

Edit. 19/10. Now suddenly **åäö** just disappeared, but now it was enoght to log out from Unity 2D and in to 3D (only rebooth did not help), and I needed to go back to 2D again cos 3D was really slow!!!

---

### Post by Azyx on 2013-12-06
Bump.
After an update of my machine with Vino-server I lost possibility to send åäö. I had to log out Unity 2D and log in to Unity 3D, and the Swedish sign åäö start to work.

BUT When I user Unity 3D on the vino-server machine, the processor work at 50-70% on both machines and many seconds long lag, so I have to go back to Unity 2D!!! Have Ubuntu 12.04LTS on both machines. I dislike Unity 2D because it is no so nice and it is impossible to have a place for needed start button in the launcher.

---

