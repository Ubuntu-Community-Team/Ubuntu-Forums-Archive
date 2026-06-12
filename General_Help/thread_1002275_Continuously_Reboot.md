---
title: "Continuously Reboot"
date: 2008-12-04
forum: General Help
---

### Post by pashonic on 2008-12-04
Is there any easy way to immediately reboot Linux once it starts up? 

I was able to setup auto-login for a user and than change the permissions via chmod of /sbin/reboot. But when I execute "reboot" in a terminal it still tells me I need to be root. I want to avoid having to do "sudo reboot" so I can run a reboot script at startup. 

I need to do this for testing purposes.

---

### Post by sedawk on 2008-12-04
If you really (really, really) want to do that, edit /etc/rc.local
and add the following line before the "exit 0"

```

echo "/sbin/shutdown -h now" |at now + 3 minutes

```

This will reboot the machine three minute after it was up and running.

I do not recommend to use a lower value because one day, you want
to turn that off again (really!).

---

### Post by pashonic on 2008-12-04
I work for a BIOS company, it's an independent installation I made today just for testing purposes. I'll give it a try.

---

### Post by pashonic on 2008-12-04
I added the following line to /etc/rc.local:

echo "/sbin/shutdown -h now"

But it is not restarting. I seriously don't care if it is messing up the OS.;)

Do you know what is going on?

Thanks for your help

---

### Post by thomas228 on 2008-12-04
> **sedawk said:**
> If you really (really, really) want to do that, edit /etc/rc.local
and add the following line before the "exit 0"

```

echo "/sbin/shutdown -h now" |at now + 3 minutes

```

This will reboot the machine three minute after it was up and running.

I do not recommend to use a lower value because one day, you want
to turn that off again (really!).

Hi
Try the referenced code and if it works change 3 to 0 and see what happens

Good luck
Tom

---

### Post by pashonic on 2008-12-04
THX all, that worked! I officially hosed my OS for the good :)

---

