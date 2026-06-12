---
title: "Frequent Problem"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by benmau5 on 2007-08-08
First off I would like to mention I am a super newb with Ubuntu. Okay and heres my problem every time i try to install a game with Cedega i get this message > Can't seem to be able to execute the WineX start up script /home/ben/.cedega/.winex_ver/winex-6.0.2/bin/winex3 - perhaps your installation of WineX version 6.0.2 is corrupted?

Can someone please help this is very aggravating.

---

### Post by misconfiguration on 2007-08-09
Ok, I realize the Cedega forums aren't very helpful I'm a Cedega subscriber myself.

Something I recommend is trying to update Cedega VIA it's front-end. Meaning you can select and action when you have opened Cedega and check for updates. If there are any download all of them and restart the app. 

I have a feeling this could update everything and help you out. Post back with results.

---

### Post by benmau5 on 2007-08-10
hmm same results :confused:

---

### Post by JesterDev on 2007-08-10
Make sure that the script exists (I'm sure it does, but just in case). Anything with a "." in front of it is going to be hidden so either use the terminal or press ctrl-H while in your home folder. 

Also make sure that the winex3 script is executable. Right click on it and choose properties and check it's permissions. You'll see a small check box down towards the bottom. Either that or use the terminal to change it's permissions:

chmod 755 winex3

---

### Post by benmau5 on 2007-08-10
how do i do all this i am very noob haha sorry

---

### Post by hikaricore on 2007-08-10
> **benmau5 said:**
> how do i do all this i am very noob haha sorry

Did you pay for Cedega?
I'm sure they bothered to provided documentation on such a simple task as updating.

---

### Post by benmau5 on 2007-08-10
yes and im not talking about the updating.....

---

### Post by benmau5 on 2007-08-12
> **JesterDev said:**
> Make sure that the script exists (I'm sure it does, but just in case). Anything with a "." in front of it is going to be hidden so either use the terminal or press ctrl-H while in your home folder. 

Also make sure that the winex3 script is executable. Right click on it and choose properties and check it's permissions. You'll see a small check box down towards the bottom. Either that or use the terminal to change it's permissions:

chmod 755 winex3



how do you do all this?

---

