---
title: "DVD Playback gone since last update (26-5-05)"
date: 2005-05-26
forum: Desktop Environments
---

### Post by Spleenie on 2005-05-26
I noted that in the latest update via kynaptic there were 3 or 4 dvd related upgrades. I cant exactly remember what they were, but I am reasonably sure libdvdcss2 was not among them.

Anyway, fast forward to today and I am not able to play DVD's any longer.

I still have libdvdcss2 installed, I have even *shudder* rebooted but to no avail.

Anyone else has this problem after upgrading recently or can help me figure this one out?

- Spleenie

---

### Post by ludi on 2005-05-26
[QUOTE=Spleenie]I noted that in the latest update via kynaptic there were 3 or 4 dvd related upgrades. I cant exactly remember what they were, but I am reasonably sure libdvdcss2 was not among them.

Anyway, fast forward to today and I am not able to play DVD's any longer.

I still have libdvdcss2 installed, I have even *shudder* rebooted but to no avail.

Anyone else has this problem after upgrading recently or can help me figure this one out?

- Spleenie[/QUOTE]
 What app are you trying to play your DVD?
Make sure you have libdvdread3, libdvdplay0, libdvdnav4 installed in your system.
Obs: That's what I have in my system.
But there are a lot of possible issues related...
Check your libs, if don't work, put more information about the problem here.

---

### Post by Spleenie on 2005-05-26
I have all the above libs installed, I use Kaffeine, totem and okle, all are complaining that libdvdcss is missing and so I cant play encrypted cds

I was able to do so before the latest update and my system still reports that I have libdvdcss2 installed and the latest version

- Spleenie

---

### Post by ludi on 2005-05-26
[QUOTE=Spleenie]I have all the above libs installed, I use Kaffeine, totem and okle, all are complaining that libdvdcss is missing and so I cant play encrypted cds

I was able to do so before the latest update and my system still reports that I have libdvdcss2 installed and the latest version

- Spleenie[/QUOTE]
 I don't know, try to remove and install libdvdcss2 or compile it by yourself.
I have no problems here (Kaffeine + Xine or Mplayer).

---

### Post by weeroona on 2005-05-31
I have also not been able to get a dvd to play since my last update. I have uninstalled libdvdcss2 and other relevent packages. I've installed and tried kaffeine, totem, ogle, xine to no avail. they are correctly pointed to /dev/dvd. the encryption seems to be what's messing up based on my unsavvy poking around. 

any suggestions would be appreciated.
-Jeff

---

### Post by tflovik on 2005-06-01
Have you edited sources.list to accept updates from other sources than the original ubuntu repositories.
I have installed all the official updates and i don't have the problems that you are describing. 
I tried to play DVD today and it worked.

---

### Post by kubuntuuser on 2005-06-02
How much detective work have you done?

What exactly was upgraded?

Were Kaffeine, totem and okle upgraded? 

or just dvd libraries which I guess these applications use?

What is the error message you are getting?

Are they official updates?

-----------------
KubuntuUser

---

