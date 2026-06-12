---
title: "Printer woes with Samba to Samba printing &amp; Cups: SOLVED"
date: 2006-03-02
forum: Desktop Environments
---

### Post by bbrand on 2006-03-02
I love Ubuntu, but why setting up a printer has to be so difficult is beyond me. I have installed 5.10, Breezy Badger on two machines at home and both had exactly the same problems setting them up to print.

Here is how I solved my problems.

First attempt was through the GUI (Gnome). I could not get foomatic gui to work because of the "root" // sudo problem.

Ok, let's try this from the terminal then.

**sudo foomatic-gui**

[I](foomatic-gui:12384): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.[/I]

I ignored this message.

I browsed the printers and the networked Samba printers (Redhat 7.2 server, my all purpose firewall/file sharing/printer server) showed up, so I thought bingo. 

I added the printer but no go. The URI kept changing to file:/dev/null and no output from the test print (with that URI no wonder). When I looked back at the terminal this was the error output:
[I]
Use of uninitialized value in string eq at /usr/bin/foomatic-configure line 328.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Foomatic/DB.pm line 3432.
lpadmin: add-printer (set model) failed: server-error-internal-error
Could not set up/change the queue "dj930c"!
Usage: /etc/init.d/cupsd {start|stop|restart|force-reload}
invoke-rc.d: initscript cupsys, action "reload" failed.[/I]

Forget this. Let's try CUPS. 

Browsed to:[http://localhost:631/printers]("http://localhost:631/printers")

Let's configure the printer I set up. 

Next issue: a root userid and password needed, and we all know what that means in Ubuntu. My userid and password did not work, it kept on cycling.

I found the solution to that problem here: 
[http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/]("http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/")

Now my userid and password allowed me access to the admin function of CUPS.

I now needed the share name for my printer, you can find that with the command: **/usr/bin/smbclient -L <server>**

Remark: My Samba server facilities are all public so no need to tell my server who I am. You might need to add the user id and password for this and other Samba related processes. I have restricted my Samba user community via IP address range as they are all behind the firewall.

The URI you need to enter in CUPS is then something like:

[I]smb://<workgroup>/<server>/<printer share name>
smb://<server>/<printer share name>
smb://<userid>:<password>@<server>/<printer share name>[/I]

Finally, it has only taken me about 3 days to figure this out, but it works. 

Hope this helps some of you out there.

---

