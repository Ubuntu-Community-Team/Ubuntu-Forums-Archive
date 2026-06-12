---
title: "Problem with shutting down a Ubuntu Linix system"
date: 2006-09-07
forum: Desktop Environments
---

### Post by sshahir on 2006-09-07
I have problem with shutting down Ubuntu Linix system from Quit dialog box.

When I click on Quit option on top right corner of desktop or System> Quit, I have four options as follows:

Logout
Lock screen
Switch user
Hibernate

But I don&#8217;t have &#8220;Shut down&#8221; option.

I appreciate for any comment why I miss &#8220;Shut down&#8221; option.

Thanks,
Shahed

---

### Post by mssever on 2006-09-07
Are you using Xgl/Compiz? I don't have a shutdown item in Compiz, but I do in the standard Metacity.

While I don't know how to get the shutdown button, I do know of a couple other options. First, you can shut down from the GDM (login) screen--at least in the theme I use. Second, you can shutdown from the terminal by using one of these self-explanitory commands:
```
sudo reboot
sudo poweroff
```

---

### Post by mikuskuikku on 2006-09-08
I have the same problem!
I used to have a 'Shutdown' button, but not any longer.
Don't know what happend when it dissapered. Have done som program-updates but still same Dapper 6.06LTS.

In a terminal I can do
```
sudo shutdown -hP now
```
but I really miss the button that does this for me (on the Quit menu).

---

### Post by sshahir on 2006-09-08
So the only way to shut down the Linux system is through command line but not GUI.

Am I right?:confused: 

The good thing is that I can , at least, shut down the system. Thanks.:) 

Regards,
Shahed

---

### Post by mssever on 2006-09-08
> **sshahir said:**
> So the only way to shut down the Linux system is through command line but not GUI.

Am I right?
You can also shut down from the login screen--depending on your theme.

Or, you could make a button on your panel:
Right click on panel > Add to Panel > custom application launcher > Name:  Shutdown; command: ```
gksudo poweroff
``` Alternate command with confirmation: ```
 zenity --question --text="Do you really want to shut down?" && gksudo poweroff
``` 
To make a reboot button, replace "poweroff" above with "reboot"

---

### Post by sshahir on 2006-09-10
> **mssever said:**
> You can also shut down from the login screen--depending on your theme.

Or, you could make a button on your panel:
Right click on panel > Add to Panel > custom application launcher > Name:  Shutdown; command: ```
gksudo poweroff
``` Alternate command with confirmation: ```
 zenity --question --text="Do you really want to shut down?" && gksudo poweroff
``` 
To make a reboot button, replace "poweroff" above with "reboot"


The first code works fine, but it asks for password each time operator wants shut down. Is there any way to elimiate the password request?

The second code works as long as entered within command line. When I use it with >Panel > custom application launcher> it doesn't work as  supposed to. I am wondering if there is any solution to a problem? If there is, can you please let me know. 

Thanks,
Shahed

---

### Post by mssever on 2006-09-10
> **sshahir said:**
> The first code works fine, but it asks for password each time operator wants shut down. Is there any way to elimiate the password request?
Actually, the second version also asks for a password (remember, though, that passwords are cached for a period of time--15 minutes, I think). I don't know how the shutdown button works, but the poweroff command requires root privileges, IIRC. You could try it without the gksudo, and if it works, then great.
> The second code works as long as entered within command line. When I use it with >Panel > custom application launcher> it doesn't work as  supposed to. I am wondering if there is any solution to a problem? If there is, can you please let me know. That's weird. I noticed it, too. And, there isn't any error message or anything.

Try this; it works for me. Save this in a file:
```
#!/bin/bash
zenity --question --text="Do you really want to shut down?" && gksudo poweroff
```
Make it executable (chmod +x filename). In the custom launcher box, use the full path to the file as the command.

---

### Post by leo_m on 2006-09-10
I have the Shut down option but it does not really shut down (shuts down all services and then just sits around, does not power off)

Maybe you can try to configure the power options a bit and then it will appear.  I got the suspend option to work using power options configuration (earlier it was missing from the menu just like your shut down option).

---

### Post by sshahir on 2006-09-10
> **mssever said:**
> 

Try this; it works for me. Save this in a file:
```
#!/bin/bash
zenity --question --text="Do you really want to shut down?" && gksudo poweroff
```
Make it executable (chmod +x filename). In the custom launcher box, use the full path to the file as the command.


It works. Thanks a lot.

Regards,
Shahed

---

### Post by mikuskuikku on 2006-09-11
But I don't think that it would be needed create own scripts and buttons to shut down poewer.
The 'Quit popup' worked fine before to power down the computer... thers been a change!
Does anybody know if I could configure some config-file to get the 'poweroff' possibility back on the 'Quit popup'? "leo_m" talked about 'power options configuration', where do I find this?

I have 2 Dapper computers, and the other computer still has the 'PowerOff' possibility (while my laptop lost it).

I tryed to figure out the name of the program/popup that gives me the "logoff, switch user, lock screen or POWER DOWN the computer" (to find out if thers any chance to get back the old version that worked fine.

---

### Post by leo_m on 2006-09-12
System|Preferences|Power Management is the interface for configuring power options, though there is no explicit UI there to decide which buttons to show up.  When I had modified my power configuration by editing settings there, the suspend button appeared...try tinkering with a few settings there and see if you get the shut down button.

---

