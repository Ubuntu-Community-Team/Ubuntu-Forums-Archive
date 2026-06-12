---
title: "Cannot change CPU frequency in xfce"
date: 2009-08-30
forum: Desktop Environments
---

### Post by dE_logics on 2009-08-30
I compiled that applet as in the xfce website...I cannot download and install from the repos cause I compiled xfce from source...so doing that will overwrite the previous compiled binaries.

But I cannot change the CPU frequency...I set it to userspace mode, and changed the frequencies in an identical manner for both the cores, but it has no effect...

I can change the CPU frequency in Gnome.

Using powernow k8 drivers.

---

### Post by tgeer43 on 2009-08-30
I can't solve your applet problem but if you just want to change frequencies then it's easy enough to do with one line of code (one line per cpu, that is).
```
echo userspace > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```Then just do the same for the other modes. I created a script for each mode and added them to a new folder in Main Menu and created a launcher for the folder in my panel. It's an unobtrusive and quick way to change frequencies - better than the regular panel applet IMO.

tgeer

---

### Post by dE_logics on 2009-08-30
I figured out how to change the scheme, but how to specify the CPU frequency in userspace mode?

---

### Post by tgeer43 on 2009-08-30
Echo the desired frequency in kilohertz to /sys/devices/system/cpu/cpuN/cpufreq/scaling_setspeed.

Example:
```
echo 800000 /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
```to set cpu0 to 800MHz.

tgeer

---

### Post by dE_logics on 2009-08-30
Every time I do this, I have to do it as a superuser...sudo won't work...

So obviously I cant make shortcuts as you say.

Any remedy?

---

### Post by tgeer43 on 2009-08-30
The commands in my scripts are prefixed with gksu and work just fine, prompting me for a password when necessary. If this doesn't work for you then I can think of only one thing at the moment.

My user is the first and only user created during the install. If the user you are operating with was added after the initial user then there are likely some permission and/or group differences between the two that are interfering.

Beyond that, I don't know what to tell you.

tgeer

---

### Post by dE_logics on 2009-08-30
Issue resolved, I changed the permission of those file, I can now change the frequency directly without elevated privileges.


No need for security to change frequency...

---

### Post by tgeer43 on 2009-08-30
Have you rebooted recently?
/sys is a virtual filesystem that is stored in kernel memory and not on disk It is recreated every time you boot up. Hence, your file permissions should not survive a reboot.

However, you could write a startup script to change the permissions after each boot.

tgeer

---

### Post by dE_logics on 2009-08-30
No i did not!!! :(

---

### Post by dE_logics on 2009-08-30
> If the user you are operating with was added after the initial user then there are likely some permission and/or group differences between the two that are interfering.

I am using the same user as it was during install, though I did change the permission.

I'll see to it.

---

### Post by dE_logics on 2009-08-30
And I do not see anything which should prevent me from changing the frequency...

---

### Post by tgeer43 on 2009-08-30
Your last two posts are not the issue anymore. You've found a way to accomplish what you want. Now you just have to deal with the fact that you'll have to reapply the permission changes each time the computer starts.

As stated previously, a startup script with the appropriate CHMOD commands should do the trick. You can either create an entirely new script and have it called during startup or just add the commands to your /etc/rc.local file where they will be automatically executed at startup for you.

If you changed the permissions using a GUI interface and are unfamiliar with the actual commands to be issued, I can help.

tgeer

---

### Post by dE_logics on 2009-08-30
No, I know all that...I've done it.

Thanks a lot! :)

---

