---
title: "How do I start Beryl?"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by hyrule_man on 2007-09-03
I can go to the settings manager, but I don't know how to actually start it up... Help?

---

### Post by abhilash82 on 2007-09-03
You can start by following these steps.

1. Start Beryl: 
> 
beryl-manager

   
2. Start Emerald (if it doesn't start on its own): 
> 
emerald --replace


3. Beryl and Emerald to automatically load at login: 
> 
System -> Preferences -> Sessions
Startup Programs -> New: beryl-manager
Startup Programs -> New: emerald --replace


4. Reboot the system.

---

### Post by hyrule_man on 2007-09-03
No I mean, I can open the Beryl manager, and change the effects and stuff. I just cant actually turn Beryl on. (As in, the red diamond icon isn't in the top right corner.)

---

### Post by PmDematagoda on 2007-09-03
You change the effects and plugins of Beryl using the Beryl Settings Manager.

---

### Post by hyrule_man on 2007-09-03
Yes, I know  this. But HOW DO I TURN BERYL ON? ALL I CAN USE IS THE MANAGER. BERYL ITSELF ISN'T WORKING, BECAUSE I DON'T KNOW HOW TO START IT.

---

### Post by PmDematagoda on 2007-09-03
Calm down, sorry for misunderstanding you.

Did you try beryl --replace after you bring up the Run application using Alt+F2?

---

### Post by PmDematagoda on 2007-09-03
As it turns out you need 2 commands to start beryl:

First start the Beryl manager using the following command as given by abhilash82:
beryl-manager

Nest start Beryl for real by entering the command:
beryl --replace

Note- You don't need to start Emerald.

Hope this helped you.:)

Also you can turn it on graphically by Application>System Tools>Beryl Manager 

when it starts up right-click on the diamond that shows up and change the window manager to beryl.

If you want it to start at start up just add the commands to the the start up programs in Sessions separately.

---

### Post by lukeheald on 2007-09-03
lol, people make things so complicated, simply open a terminal and type beryl

---

### Post by FuturePilot on 2007-09-03
Beryl Manager>Select Window Manager>Beryl
Emerald should start automatically. You only need to use the emerald --replace command with Compiz Fusion.
Then in the Sessions panel just add beryl-manager

---

### Post by alantorem on 2007-10-03
> **abhilash82 said:**
> You can start by following these steps.

1. Start Beryl: 

   
2. Start Emerald (if it doesn't start on its own): 


3. Beryl and Emerald to automatically load at login: 


4. Reboot the system.


Hi I was wondering how to start beryl like a start up file as well. I tried the description you have above. I have Feisty if that makes any difference. Anyway Beryl wont start up at login, any suggestions?

---

