---
title: "apache2 and mysql-server startup worries!"
date: 2011-03-26
forum: Desktop Environments
---

### Post by snisarg on 2011-03-26
i am us ubuntu 10.10 and just installed apache2 and mysql-server.
It is really annoying to find that both these applications are already running on startup.

Is there a way to keep it disabled on startup, and start it if needed via the terminal only?

---

### Post by snisarg on 2011-03-27
please!
can anyone tell me how do i disable apache2 and mysql from startup?

---

### Post by SeijiSensei on 2011-03-27
sudo  update-rc.d apache2 disable

I think the same process applies to mysql-server, though I don't have a running copy here to test it.  Ubuntu has been making a transition to using "upstart" for server daemons, but not all of them have been converted to this method.

You can do this manually by repointing the symlinks in /etc/rc[0-6].d/ which is what update-rc.d does.  Here's the output for that program for Apache:

 Removing any system startup links for /etc/init.d/apache2 ...
   /etc/rc0.d/K09apache2
   /etc/rc1.d/K09apache2
   /etc/rc2.d/S91apache2
   /etc/rc3.d/S91apache2
   /etc/rc4.d/S91apache2
   /etc/rc5.d/S91apache2
   /etc/rc6.d/K09apache2
 Adding system startup for /etc/init.d/apache2 ...
   /etc/rc0.d/K09apache2 -> ../init.d/apache2
   /etc/rc1.d/K09apache2 -> ../init.d/apache2
   /etc/rc6.d/K09apache2 -> ../init.d/apache2
   /etc/rc2.d/K09apache2 -> ../init.d/apache2
   /etc/rc3.d/K09apache2 -> ../init.d/apache2
   /etc/rc4.d/K09apache2 -> ../init.d/apache2
   /etc/rc5.d/K09apache2 -> ../init.d/apache2

Entries that start with an S are activated at boot; those with a K are not.  So to disable apache2, update-rc.d repoints all the symlinks to begin with K09. The numbers control the order of execution.  Apache has an S91 because it starts late in the boot process; conversely it has K09 for shutdown so it will be stopped early in that process.

---

### Post by snisarg on 2011-03-29
Thank you for your reply.

what are these folders exactly.

rcX.d? are these the links to all the processes that are started out during boot? 
and can i just rename the links to Kxxxxx from Sxxxx to disable them during boot?

---

### Post by snisarg on 2011-03-29
there is an entry in the folder for init.d for mysql, but noting in the rc[0-6].d
how do i disable that!

---

### Post by SeijiSensei on 2011-03-29
It's probably running with Upstart.  Do a Google search for "ubuntu upstart" and see if it answers your question.

---

### Post by snisarg on 2011-03-30
Oh thank you! 
that totally helped me.

---

