---
title: "Printing Manger lock up"
date: 2005-06-27
forum: Desktop Environments
---

### Post by vtechstu on 2005-06-27
When I open the Printing Manager to add a printer, it just says "initializing manager" and nothing happens.  It just sits there with that.  It won't close and I can't get anything loaded! 

Tryed rebooting and did same thing again.  After like a half hour it closes and a window appears saying

"Unable to retrieve the printer list.  Connection to the cups server failed.Check that the cups server is correctly installed and running. Error connection refused."



[B]
UPDATE:[/B]   I get this error when trying to install printconf from repositories.

Setting up printconf (0.7.4.2ubuntu1) ...
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 99!
invoke-rc.d: initscript cupsys, action "force-reload" failed.

And still having same error.  HELP!

---

### Post by nebula on 2005-09-22
[QUOTE=vtechstu]When I open the Printing Manager to add a printer, it just says "initializing manager" and nothing happens.  It just sits there with that.  It won't close and I can't get anything loaded! 

Tryed rebooting and did same thing again.  After like a half hour it closes and a window appears saying

"Unable to retrieve the printer list.  Connection to the cups server failed.Check that the cups server is correctly installed and running. Error connection refused."



[B]
UPDATE:[/B]   I get this error when trying to install printconf from repositories.

Setting up printconf (0.7.4.2ubuntu1) ...
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 99!
invoke-rc.d: initscript cupsys, action "force-reload" failed.

And still having same error.  HELP![/QUOTE]
 I have the same thing. I guess it happened when I installed gimp-print to use the escputil for my HP printer. (which doesnt work anyway

---

### Post by manubreizh on 2005-09-23
i've had the same stuff and found out what is messed up : i have usb modem connection (with speedtchfull debian package)(home) and had configured an ethernet connection (work) editing /etc/network/interfaces : to enable ethernet, i must comment one line in etc/network/interface , the last one : iface eth0 inet ;
 doing this, cups is recognized and printing works fine ; 
if this line is uncommented and ethernet interface disabled, cups cannot work, and i have the same trouble than you.
that's not a real answer for geeks i think , but i'm sort of a newbie and it's working fine !
hope it helps

---

### Post by nebula on 2005-09-27
hmm that way I would disable my network card with actually connects me to the internet so I don't think that is an option form me ;)

---

### Post by Paperjam on 2005-09-28
Please try:
Open *[http://localhost:631/](http://localhost:631/)* in a web-browser. Does it show the cups configuration-page?

If **yes**, try removing the KDEPrint config-file (but only if that web-page is displayed!) and restart the KDE Print-Manager:
```
rm .kde/share/config/kdeprintrc
```

If **not**, do
```
ifconfig
```
Is the "lo"-device shown?
If not, try:
```
sudo ifconfig lo up
```
and restart networking as well as cups (the printing system) with
```
sudo /etc/init.d/networking restart
sudo /etc/init.d/cupsys restart
```

Retry if *[http://localhost:631/](http://localhost:631/)* is displayed in a browser.

---

### Post by nebula on 2005-09-28
Perfect! The 631 port is resonding, threw away mij rc file, added my printer and... It's working again! That one bug less on my to fix list :P 
Cheerz Nebula

---

### Post by Paperjam on 2005-09-28
[QUOTE=nebula]Perfect! The 631 port is resonding, threw away mij rc file, added my printer and... It's working again! That one bug less on my to fix list :P[/QUOTE]
Actually, I don't think the problem is entirely resolved. After the next boot, it might be back, because this was more a workaround than a fix...

---

### Post by Divan Santana on 2005-11-10
hey everyone!

I had this prob too on buddys of mine pc!He installed gimp, wonder if that broke it. Doing a sudo ifconfig lo up fixed it but was only temp.

Not sure how to make it permanent but added a S99local in /etc/rc2.d and added ifconfig lo up command to it which should of fixed it!

---

### Post by gamma on 2006-02-08
I'm getting an error message saying that cups can't be contacted. Lo is up, cups is running, and I can access cups on localhost:631. This is on dapper... any ideas?

---

### Post by robert114 on 2006-02-28
I'm having the same problem but i have a cups log full of errors like these:
E [28/Feb/2006:12:56:51 +0100] cupsdAuthorize: Local authentication certificate not found!
I [28/Feb/2006:12:57:54 +0100] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=11213)

edit:
I have solved my printing problem alltoug i'm not sure what actualy helped me.

first i removed the .kde/share/config/kdeprintrc file, whithout any result
second i tried the gnome gnome-cups-manager (whitch worked for me, i could install a printer but it wouldn't work on KDE)
After a reboot the printer also showed up on Ubuntu and worked, but when i print it uses up to 100% CPU so i'm looking further for a good solution!

---

