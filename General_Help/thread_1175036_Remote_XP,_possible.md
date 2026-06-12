---
title: "Remote XP, possible?"
date: 2009-05-31
forum: General Help
---

### Post by PaganImmolator on 2009-05-31
I guess I am asking if this is possible. I can't get itunes to work right under a virtual environment. Keep having issues with syncing. Itunes just sits there and syncs forever.

Is it possible to set up a headless XP box and remotely control it from within Ubuntu? Kind of the way the remote desktop app works under windows.

This iTunes thing is really a dealbreaker for my wife who I am trying to convert to Ubuntu.

---

### Post by arubislander on 2009-05-31
Ubuntu comes with a terminal server client. You can find it under Applications->Internet->Terminal Server Client
If you've ever used the Windows equivalent you'll find this one easy to use.

---

### Post by tbullock on 2009-05-31
I could not get the server client to work when I did this. You may try from the terminal: ```
rdesktop your.i.p.address
``` Where "your.i.p.address" is the ip for the destktop pc. That worked for me without a hitch if your XP box has a password and you have it setup to allow the remote connection. You will need a monitor, keyboard, and mouse on the desktop to get the ip but after that you should be fine.

---

### Post by PaganImmolator on 2009-05-31
Just to be clear. That terminal server will connect and display the XP GUI? I assume I need to install some sort of server on the XP box?

---

### Post by mpsii on 2009-05-31
In XP, you have to go to System Properties and click on the Remote tab. Make sure you have checked the Remote Desktop section's "Allow users to connect remotely to this computer". And, then, be sure to click the Remote Users box to allow specified users to connect.

---

### Post by PaganImmolator on 2009-05-31
Thanks guys, I will give it a whirl tonight

---

### Post by bacardiandwatermelon on 2009-05-31
What I did was have realvnc on the xp box, then use ubuntu's Terminal Server Client to connect to it... Its always a good idea to password protect the vnc.

---

### Post by HermanAB on 2009-05-31
WinXP Pro has RDP built in.  It is secure.  See this:
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

---

### Post by bacardiandwatermelon on 2009-05-31
Yeah it does, but I think it only allows 1 connection and I think from memory it logs the user out aswell. But I can't remember its been ages since I have used it :)

---

### Post by PaganImmolator on 2009-05-31
> **bacardiandwatermelon said:**
> Yeah it does, but I think it only allows 1 connection and I think from memory it logs the user out aswell. But I can't remember its been ages since I have used it :)

This sounds about right from what I remember from my experience with XP. Also the account being accessed needs to have a password enabled or it wont work either.

---

