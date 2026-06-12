---
title: "modprobe hack at startup puzzle"
date: 2010-10-31
forum: Desktop Environments
---

### Post by crong on 2010-10-31
I'm using 10.04 with Gnome and I've just discovered that Kaffeine works with my TV card provided I use the modprobe hack. So I created /bin/dtvfix with the following:

```
#!/bin/bash
/sbin/modprobe -vr dvb_bt8xx
/bin/sleep 5
/sbin/modprobe -v dvb_bt8xx
```and it works just fine when invoked manually: sudo dtvfix

So far, so good. The part I'm stuck on - which I thought would be trivial - is how to get this to run automatically at startup.

[LIST]
[*]I tried putting it in System > Preferences > Startup Applications
[*]I tried putting it in rc.local
[*]I tried running it as a root cron job: @reboot /usr/bin/sudo dtvfix
[/LIST]
but all to no avail.

---

### Post by Bobhuber on 2010-10-31
Sounds like a problem with the file properties and ownership.

---

### Post by crong on 2010-11-01
Thanks for replying Bobhuber, but what you say doesn't actually help me in any way.

---

### Post by Bobhuber on 2010-11-01
OK may be I assumed to much.
Try this.
Remove the path statements from the modprobe commands.
#!/bin/bash
modprobe -vr dvb_bt8xx
sleep 5
 modprobe -v dvb_bt8xx

Save the file dtvfix.sh  in your home directory. 
Make sure the permissions are correct - sudo chmod 755 dtvfix.sh
Create a new startup file in - System > Preferences > Startup Applications
Run this command - sh /home/<yourdirectory>/dtvfix.sh 

I dont have a tv card to try all this but it should work.

---

### Post by crong on 2010-11-01
Yes, sorry. I'm not exactly a noob but there is so much I don't know.

Thanks for the suggestion. I followed the steps exactly but, like the other methods, it didn't work.

I've got a feeling that the script is actually running ok and that maybe something happens after it's run to cancel out what it did.

Is there a way of verifying that the script ran without errors? (Sorry I don't now how to do this).

---

### Post by Bobhuber on 2010-11-01
Me too.
I really wasn't paying any attention to the modprobe commands. Are you trying to remove and then reinstall the module? 
modprobe -r (remove) dvb_bt8xx    (would remove the module)
modprobe -v (verbose) dvb_bt8xx (would reinstall the module and show any errors)
modprobe -v -r  dvb_bt8xx    ( would remove and show errors)
I have no idea what modprobe -vr (???)  dvb_bt8xx
modprobe -s (output errors to system log) dvb_bt8xx (this will install the module and output errors to the system log which you can then look at after boot)
Also not sure how modprobe works during a boot sequence but that should get you started.

man modprobe

---

### Post by crong on 2010-11-01
Yes, someone discovered that removing and reinstalling the module makes it start working. Of course, you are correct that the -v option is redundant when being run at startup (and -vr is simply shorthand for -v plus -r). But I have found something:

This is the contents of dtvfix.sh at the moment:

```
#!/bin/bash
modprobe -r dvb_bt8xx
sleep 5
modprobe dvb_bt8xx
```and, when run using sudo sh divfix.sh it (runs silently and) writes it's activity to the syslog and it works.

But when invoked during startup I get this in the syslog instead:

```
modprobe: FATAL: Error removing dvb_bt8xx (/lib/modules/2.6.32-25-generic/kernel/drivers/media/dvb/bt8xx/dvb-bt8xx.ko): Operation not permitted
```So far I'm not having much luck discovering what "Operation not permitted" means exactly.

---

### Post by ironic.demise on 2010-11-01
Try giving ownership to root?

---

### Post by Bobhuber on 2010-11-01
I think I found your answer and an explanation (or at least the same problem)here.
It looks like all you have to do is reload the module at boot
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-05/msg02214.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-05/msg02214.html)
Edit the file /etc/modules
Add a single line with the name of your module (name only) to the file,save it and reboot.

dvb_bt8xx

---

### Post by crong on 2010-11-01
@ ironic.demise: Changing the owner to root got rid of that error message but no activity replaced it and it didn't work.

@ Bobhuber: I disabled the startup script and tried it anyway but it didn't work. (I am quite sure the module was loading automatically because I can see in syslog  the same reports as I get when reloading it manually. BTW, I don't know why this hack works.)

Well, if we can't do it, we can't do it - the TV card works and all I have to do is reload the module manually once per session so it's a minor inconvenience.

It's just that I thought running a startup script like this would be the easy part.

---

