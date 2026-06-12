---
title: "Right Click &quot;run as&quot; option for applications"
date: 2010-02-25
forum: Desktop Environments
---

### Post by ericmarlow on 2010-02-25
Is there a graphical desktop which includes a right click "run as" option for launching applications as root? 
 
Alternatively is there one which enables the creation of a desktop icon which runs the application with root privileges? 
 
At present I have to log on as root, or open the terminal and type in a gksudo command to use the  gui application, which will not work at all without root privileges. Admin privileges alone are not enough.
 
Regards,
 
Eric

---

### Post by Hero of Time on 2010-02-25
Can't you add custom actions to Nautilus? If so, then add the custom action to run 'gksu $1', or whatever, to start a program that way. Open files can be done with something like 'gksu gedit $1' to open a file in gedit as root.
Same applies for desktop launchers, create a launcher for a program and add gksu before the command.

---

### Post by Kakers on 2010-02-25
You could use your panel 'Add to Panel' -> 'Custom Application Luancher' or drag the program onto your panel from you menu and before the command that launches the program put 'gksu' 'gksudo' or 'sudo' and that should open the program every time like that without having to do it through the terminal, all you will have to do is put in your password.

Hope this helps.

---

### Post by ericmarlow on 2010-02-25
> **Kakers said:**
> You could use your panel 'Add to Panel' -> 'Custom Application Luancher' or drag the program onto your panel from you menu and before the command that launches the program put 'gksu' 'gksudo' or 'sudo' and that should open the program every time like that without having to do it through the terminal, all you will have to do is put in your password.
 
Hope this helps.
 
Thank you Kakers. 
 
I could not find "Add to panel" or "Custom application launcher", but I did discover that:
 
"Right click" on desktop brings up "Create launcher" option.
Enter the terminal command line in the box eg "gksudo /usr/bin/applicationname"
and hey presto you get an icon which does the job.
 
Very impressive answer for a 9 beaner!!!
 
Regards,
 
Eric

---

### Post by Kakers on 2010-02-25
Thanks haha,

Still pretty new to Linux myself, started using it back in like May last year. Guess it helps having to use it 5 days a week and support others as well.

Perks of an IT job I guess :o Always end up on here find out solutions to problems other people have gotten and today just said "Stuff it, I'm creating an account" haha

---

