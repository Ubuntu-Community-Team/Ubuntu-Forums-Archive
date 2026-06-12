---
title: "Login Window not showing up"
date: 2006-10-27
forum: Desktop Environments
---

### Post by bleearg on 2006-10-27
Hi all,
I'm pulling my hair out because I have no idea why my system suddenly started to hate me this evening.

I'm running Kubuntu on Dapper Drake 6.0.6 LTS.  I made the mistake of logging out of KDE and starting up a Gnome session this evening, in an attempt to make an application work that was crashing in KDE.  Ever since then, my system keeps booting into Gnome and it's driving me nuts.  It won't give me the option to boot into KDE, even if I choose "Log Out" from the task bar button.  I cannot change the settings from the "Login Manager" because it won't start up.  When I select it, my cursor mocks me for about three seconds, then poof...nothing appears.

So far, this is what I've done:

1.  Tried uninstalling gdm and reinstalling.
2.  Tried 'sudo gdmsetup'.
    - I get "Could not access GDM configuration file."
3.  Tried replacing my 'gdm.conf-custom' file.

I had Auto Login enabled in KDE.  Is there a way to disable the auto login feature without using the damn Login Window application that won't seem to load?

TIA,
evt

---

### Post by fguilhon on 2006-10-27
Well.. the auto login feature is on GDM.. so you have to edit the config file.
> 
sudo gedit /etc/gdm/gdm.conf
Look for AutomaticLoginEnable and set it to false...

I think you should give GNOME a chance.. it's a very nice WM..
good luck!

---

### Post by bleearg on 2006-10-27
Hi, thanks for the quick reply.  

GNOME is nice, but I much like the configurability and look of KDE.  I did find the gdm.conf file and it is set as you mention above.  After poking around with this some more, I believe my problem to actually be with 'kdm' and not 'gdm'.  I've figured out that kdm is my default display manager:

cocytus:~$ cat /etc/X11/default-display-manager
/usr/bin/kdm
cocytus:~$

Would kdm be the one handling the auto login, then?

---

### Post by bleearg on 2006-10-27
I feel like such a tool now...:???: 

It took me all of about 30 seconds to find the option in the 'kdmrc' file.  If only I had noticed kdm was my default earlier... ](*,)

---

### Post by fguilhon on 2006-10-30
I've never used Kunbuntu so I didn't know it wasn't GDM..
But I think they(kdm and gdm) are pretty similiar.. 
It has to be a kdm.conf somewhere. :P
Anyway, it's good to know that you solved your problem!

---

### Post by alican timur on 2006-12-03
i have the same problem. i mean, i have the login window showing up at the beginning, but i can't open it up from gnome. the same thing happens to me. the system seems busy for like 2 seconds, then nothing happens. help please?

---

