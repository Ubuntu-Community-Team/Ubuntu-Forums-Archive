---
title: "KRDC / Desktop Sharing Hacked???"
date: 2009-03-21
forum: General Help
---

### Post by sukumade on 2009-03-21
Note: I posted this on the Kubuntu.org forums as well, but considering the circumstances, I figured I would post here too.

I am a bit new to Linux and installed Kubuntu a few days ago. In the process, I enabled Desktop Sharing. I opened the ports on my router to allow connections from the outside. However, I made sure to set a password (and it was a strong one). I set it to allow uninvited connections. I did this so I could access my PC remotely. This was only going to be temporary until I setup a more secure solution.

Anyways, I woke up this morning and noticed the KRDC icon in my system tray was lit up (meaning someone was connected) and my system was running slower than normal. I hovered over the icon and it said there was a connection from an IP I did not know. I did a WHOIS search and discovered it belonged to an ISP in Korea. Obviously this wasn't anyone I knew. I have since disabled remote connections and am typing this from a different computer.

My questions are:

1. Does the KRDC icon light up if someone is TRYING to authenticate, or only when someone has SUCCESSFULLY connected?

2. Seeing as how I had a presumably secure password (over 13 characters long with upper, lower, numbers, and symbols) how would this be circumvented?

3. If someone did indeed succeed in infiltrating my system, what steps should I take next?

Thank you in advance for any help and advice.

---

### Post by srt4play on 2009-03-21
> **sukumade said:**
> If someone did indeed succeed in infiltrating my system, what steps should I take next?

Format and reinstall. You have no idea what could be lurking on that system. That said, I would first make an image of that system to maybe load onto a spare machine that is not connected to the network for detailed analysis.

---

### Post by hikaricore on 2009-03-21
> **srt4play said:**
> Format and reinstall. You have no idea what could be lurking on that system. That said, I would first make an image of that system to maybe load onto a spare machine that is not connected to the network for detailed analysis.

I don't think that's necessary..

More than likely you just need to change your password and in the future run KRDC on a non standard port.
For example I ran mine for awhile on port 4321 after seeing a number of failed connections from Asia and South America.

---

### Post by sukumade on 2009-03-21
> **hikaricore said:**
> I don't think that's necessary..

More than likely you just need to change your password and in the future run KRDC on a non standard port.
For example I ran mine for awhile on port 4321 after seeing a number of failed connections from Asia and South America.

Thanks for the replies...

I could change the port which would create security by obscurity, but even more disturbing is the fact that my password was circumvented. I chose a password I have not ever used anywhere else and it was quite complex. I know my system is up to date with the latest patches (Intrepid with KDE 4.2), so it really concerns me that there could be an issue with KDRC itself. I'm not saying it is impossible for someone to get my password, but highly unlikely. I will probably reinstall, but this does make me wonder if I should even use KDRC in the future. Does anyone have any suggestions for a better and more secure remote desktop solution for linux? Thanks!

---

### Post by sukumade on 2009-03-21
OK, I just found out the solution and cause for this. 

There is a bug per se in KDRC that makes the icon light up even if someone isn't successfully authenticated.

To test this out, I used my wife's laptop and installed VNC. I connected to my computer without putting in the password and the icon lit up saying that it had authenticated. However, when I put in a bad password and got an authentication failure, the icon remained lit. Even if I put in the correct password and connect, then disconnect the icon remains lit.

A bug for sure, but I'd rather have a bug than a hacked computer. I will be changing the port and looking into more secure remote desktop options. Thanks again for the help!

---

### Post by srt4play on 2009-03-21
> **hikaricore said:**
> I don't think that's necessary..

In my case a couple scripts were downloaded to a hidden directory in my home folder. I feel it would have been irresponsible to just delete them and assume the machine was then clean.

---

### Post by hikaricore on 2009-03-21
> **srt4play said:**
> In my case a couple scripts were downloaded to a hidden directory in my home folder. I feel it would have been irresponsible to just delete them and assume the machine was then clean.

Still suggesting a format and reinstall is not a solution we like to see around here.
At the very very most the user should wipe his home folder after backing up any important data.

This saves said user from having to reinstall everything on their system.

---

