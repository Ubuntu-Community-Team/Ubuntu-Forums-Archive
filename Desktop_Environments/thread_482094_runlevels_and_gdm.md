---
title: "runlevels and gdm"
date: 2007-06-23
forum: Desktop Environments
---

### Post by tcv on 2007-06-23
Hey folks,

A couple of weeks back, I forced Ubuntu to throw me at command-prompt for login. I did it on purpose. I removed in the symlink to gmd in /etc/rc2.d/. 

I know how to fix it. So, it's not a big deal.

What I am wondering is how to change default display managers and how that affects that particular symlink, if at all.

I've read elsewhere that I can change the default *DM, by editing the content of /etc/X11/default-display-manager.

But if gdm starts at runlevel2 via that symlink, wouldn't gdm STILL start if I put that symlink back in place? What if I wanted to switch to something else? How would I force Ubuntu to start a different display manager upon bootup instead of what I have now (text login, sudo kdm start)

Any help understanding this is appreciated.

Cheers,

Mike Whalen

---

### Post by tcv on 2007-06-23
Well, I just found out that putting a symlink S30kdm and pointing it /etc/init.d/kdm doesn't, ahm, do anything different to the login. But I can login via a command prompt and start kdm. Hmmmmm....

---

### Post by tcv on 2007-06-23
Ah, I figured this out.

As I mentioned before, I knew that if you changed the default-display-manager under /etc/X11/ to reflect what you wanted your display manager to be.

But still when I placed the symlink for either S30gdm or S30kdm in /etc/rc2.d, I would still drop to a text login.

I found the following was wrong:

1. When the default display manager was gdm, default-display-manager had a path of /usr/sbin/gdm. kdm gets placed in /usr/bin/. So that path was wrong. I fixed it.

2. Secondly, I now understand better that the gdm and kdm scripts both honor what is set in default-display-manager and the scripts won't run unless what the script matches what's in the default file. So, if your default-display-manager says "/etc/bin/kdm" and you try to run sudo '/etc/init.d/gdm start', the script aborts stating that the default display manager is NOT gdm, which is isn't.

So, once I fixed the paths, I could test the script to make sure kdm would launch. 

'sudo /etc/init.d/kdm start' worked. So, I recreated that symlink in /etc/rc2.d to 'S30kdm'.

And now it starts. 

In doing that, I am better understanding how to switch between display managers and desktop environments, too! :-)

Cheers,

Mike...

---

