---
title: "How do I remove autostart applications?"
date: 2011-01-29
forum: Desktop Environments
---

### Post by JimGvo on 2011-01-29
Now the title suggests that the solution is simple.  Either go to System/Preferences/Preferred Applications or look in .config/autostart but that's not the solution to my problem.  I accidentally somehow saved my desktop so on login now I get a bunch of windows automatically opened that I don't necessarily want.  I can't figure out where that info was saved nor how to remove items from the list. Running Gnome and Ubuntu 10.04 

Thanks,
Jim.

---

### Post by ajgreeny on 2011-01-29
Shutdown everything so you just have the basic gnome desktop running, nothing else, then go to startup applications listing in System ->Preferences ->Options tab and click to remember running applications, and put a tick in the "Remember running applications when logging out".

Now close that window, and logout, and back in again, open the startup applications window -> options tab again, remove the tick mark, and you should be good to go.

---

### Post by JimGvo on 2011-01-29
Great!  Thank you!

Jim

---

### Post by sloopjonb on 2011-05-23
How do I make this change in 11.04 with Unity? I want a couple of terminal windows to be there when I log in, but nothing lasts across a logout/login.

Is there a preference where I can set this?

Best wishes,

Jon

---

### Post by Frogs Hair on 2011-05-23
You could make a script in Gedit and make executable by right clicking going into properties and save as .terminal_start_script (example) it will saved in hidden folders.

Here is a sample of a start script for Conky  . The line that says sleep represents a time that can be changed . This allows the other startup applications such as Compiz to be running before Conky starts. I have not tried this with other applications , but I sure you can find someone to help. 

Example :```
#!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
```

---

### Post by sloopjonb on 2011-05-23
Hi,

Thanks for the suggestion, but the idea of having to write scripts for each and every application/terminal window that I'd like to have open at login, is just crazy. 

I don't mean your suggestion is crazy, just that having to resort to something like this to restore functionality to Gnome/Unity is crazy.

Best wishes,

Jon

---

### Post by Frogs Hair on 2011-05-23
> **sloopjonb said:**
> Hi,

Thanks for the suggestion, but the idea of having to write scripts for each and every application/terminal window that I'd like to have open at login, is just crazy. 

I don't mean your suggestion is crazy, just that having to resort to something like this to restore functionality to Gnome/Unity is crazy.

Best wishes,

Jon

Ok , I see what mean now . There are a number of applications on the startup application list that start but do not open automatically with exception of applications that were written to do so. The applications you want to open automatically may not include that option , so that is why some use a script. The option to autostart an application is usually in preferences if if it has that option.

---

