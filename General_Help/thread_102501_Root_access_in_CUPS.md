---
title: "Root access in CUPS ?"
date: 2005-12-12
forum: General Help
---

### Post by tuxy on 2005-12-12
I am trying to install my printer by logging into CUPS management system by typing in [http://127.0.0.1:631](http://127.0.0.1:631) but, when I try to manage printers or do the other stuff it asks for User-id and password to do have the root the privileges. 

But, in Ubuntu there is no root password and everything works through "sudo" stuff. But, sudo is used only at command console right? Then what I have to enter for user-id & password for the stuff I am doing? I have tried typed in the normal user and password which I type in at command console when it asks for sudo in CUPS. But, no luck!!!

I did install the printer through the usual System>Admin>Printing but I want to do some extra stuff through CUPS way.

Any clues? Quick help will be greately regarded.

---

### Post by schilcha on 2005-12-12
You can *activate* your root-account by typing ```
sudo passwd
```. You can then supply a pwd for root and use it to login as root (via http or at the console). Don't ask me what this means in terms of security -- I think it's handy to work as root from time to time when applying major changes to the system.

---

### Post by tuxy on 2005-12-12
Thanx for the quick reply. But, unfortunately it didn't work!! :(

---

### Post by schilcha on 2005-12-12
What didn't work? 

If you mean changing the pwd, you might be right... I looked at [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo") and found that the correct command is:
```
sudo passwd root
```

If you mean configuring your printer, I can't help you. If I go to [http://localhost:631/](http://localhost:631/), I get the message ```
Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing
```

How did you manage to enable the administration interface?

---

### Post by hajk on 2005-12-12
You can edit /etc/cups/cupsd.conf by commenting out the lines
``AuthType Basic'' and ``AuthClass System'' near the end of the file.
Now you have access to [http://localhost:631](http://localhost:631) without any passwords...

---

### Post by tuxy on 2005-12-12
What I meant is I have changed the root password but I couldn't get into the CUPS through the web browser. Even I got the same message you got "Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing)." I couldnt log in to Admin tasks!!!



[QUOTE=schilcha]What didn't work? 

If you mean changing the pwd, you might be right... I looked at [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo") and found that the correct command is:
```
sudo passwd root
```

If you mean configuring your printer, I can't help you. If I go to [http://localhost:631/](http://localhost:631/), I get the message ```
Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing
```

How did you manage to enable the administration interface?[/QUOTE]

---

### Post by jimmy41 on 2005-12-13
[QUOTE=hajk]You can edit /etc/cups/cupsd.conf by commenting out the lines
``AuthType Basic'' and ``AuthClass System'' near the end of the file.
Now you have access to [http://localhost:631](http://localhost:631) without any passwords...[/QUOTE]


Just came across this problem today (linux noob).  Exactly what I needed.  Thanks!

---

### Post by chk9 on 2005-12-21
Though not secure it works, however I wanted something better and found it in
[http://localhost:631/sam.html#PRINTING_SECURITY]("http://localhost:631/sam.html#PRINTING_SECURITY")

I followed the manual and issued:
> sudo lppasswd -a <me>  

and edited 
 > sudo vi /etc/cups/cupsd.conf  
with the following entries:
> 
<Location />
AuthType Digest
AuthClass User
Order Allow,Deny
Allow From 127.0.0.1
Deny From All
</Location>


And I made sure all other </Location> lines were commented out.

Lastly I restarted CUPS
> sudo /etc/init.d/cupsys restart

And all is working now :-)

Have Fun, C

---

