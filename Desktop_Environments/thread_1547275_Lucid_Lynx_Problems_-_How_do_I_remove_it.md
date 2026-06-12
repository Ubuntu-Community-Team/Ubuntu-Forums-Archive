---
title: "Lucid Lynx Problems - How do I remove it?"
date: 2010-08-06
forum: Desktop Environments
---

### Post by KarmicKlot on 2010-08-06
I had a good working setup in Karmic Koala, and made the mistake of downloading Lucid Lynx.  Now every time I turn on I have to put in my default keyring passwod and my user password.  In addition I cannot connect to my own BT Home Hub.  The name of my home hub appears, and I can disconnect and re-connect, but Firefox cannot load any webpage.  In short the "upgrade" has rendered the laptop useless except when booted to Windows.
 
How can I get rid of the Ubuntu installation completely, without damaging Windows, and if possible restore the Windows partition to its original full size?  If I can do that I will try to reinstall and configure Karmic Koala.

---

### Post by a77ssii on 2010-08-06
Second this, I had Karmic up and running with no issues.  "Upgraded" to Lucid and everything's gone to hell in a bucket.  How do I remove Lucid and go back to Karmic without data loss?

---

### Post by infamous-online on 2010-08-06
The answer to both of you guy's problem is this! System > Preferences > Then click on Startup Applications Preferences and uncheck these two Secret Storage Service & SSH Key Agent. That will get rid of the keyring issues now the issues with the wireless, I can't help you on both I can ask what are you using built-in wireless or a pc card? If you're using a pc card then the connection will die every few minutes for whatever reason, cause I can't keep it connected unless I am on windows like you guys have stated, but under Ubuntu it won't stay connected. I have a laptop with built-in wifi and it has no issues whatsoever, that's why I was asking if you're using a pc card or built-in BT wireless?

---

### Post by KarmicKlot on 2010-08-07
I have built in wifi, which was never a problem in Karmic Koala, but would not download even a single web page in Lucid Lynx.  I have done what you suggested, and now Firefox is working!

---

### Post by a77ssii on 2010-08-07
Did exactly as you suggested and still a PITA.  Almost every update fails, it takes about 20 minutes and the warning stating about 90% of the updates failed pops up.  I never had this issue with Karmic, at this point I'm about ready to just disable automatic updates since none are successful anyway and just hope everything keeps working right.

---

### Post by KarmicKlot on 2010-08-08
I have not tried updating yet, but using the web is a PITA, as it requires me to put in my router authentication key every time I want to connect, then drops the connection every few minutes, and requires the key again.  Is there any way of making it remember the key and log in automatically?  
For me the big use of Ubuntu on the laptop was that in Karmic Koala I could get a quick and stable internet connection when I was using the laptop on my boat and connecting to public networks, most of which needed access keys.  It is also still asking for my admin password at random intervals.

---

### Post by KarmicKlot on 2010-08-08
I unchecked Secret Storage Service & SSH Key Agent, and that allowed me to work a little, and I even managed to connect to the Internet last night.  Today despite both being unchecked the only improvement is that it no longer asks for my "default Keyring" password.  The Internet is unusable because it drops the connection and forces me to input my router key every couple of minutes. I have tried to run Update Manager, which has failed to download even a single update.  I am of course having to write this on a Windows machine.  I have tried putting my wireless router key into Network Manager, but it is never saved.

---

### Post by infamous-online on 2010-08-10
Well I see this seems to be an issue with the wireless drivers, as stated with my Dell laptop with wifi built-in the connection remains connected, but with my older old Dell laptop with a pc card the connection won't stay connected. However that same laptop with XP, Vista, or Windows 7 on it works just fine with that pc card, it's with the drivers on Linux preventing the connecting from staying constant, so I'll dig around to find some more info about it and post my results as I want this solved as well.

---

