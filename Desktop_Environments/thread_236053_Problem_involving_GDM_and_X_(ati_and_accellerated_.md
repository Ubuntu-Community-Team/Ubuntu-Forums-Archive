---
title: "Problem involving GDM and X (ati and accellerated graphics too)"
date: 2006-08-14
forum: Desktop Environments
---

### Post by nibbo on 2006-08-14
Hi

I am running ubuntu on my desktop computer trying to get rid of windows (nowdays i only boot windows for games) but i have one small problem.
When i start and login thru gdm my accelerated graphics wont work, for example i cant use gimp or amarok, glxgears laggs and fglrxinfo gives me errors. With some testing i found out that if i kill X by hammering ctrl + alt + backspace and then start it with the startx command it all works. So i have been doing that for a while now but I am getting kind of sick of it not working as it should.

Is it possible to fix gdm to correctly load the graphics stuff? If it is, how?

And if not, how do i prevent gdm from starting?

---

### Post by baka_rob on 2006-08-14
Just out of curiosity, what are the errors given by fglrxinfo?  Is gdm/X for some reason not loading your driver?  This link will be largely irrelevant (suse), but shows they also ran glxinfo:

[http://linux.wordpress.com/2006/05/12/suse-101-ati-drivers-installation/]("http://linux.wordpress.com/2006/05/12/suse-101-ati-drivers-installation/")

does the glxinfo command show the same output?  Does it give you errors as well?

If you wanted to disable gdm, you may want to consider changing /etc/inittab to use runlevel 3.  You would make a change similar to the following:

From:
```
# The default runlevel.
id:2:initdefault:
```
To:
```
# The default runlevel.
id:3:initdefault:
```

followed by a save and reboot.  You may need to use su or sudo to edit and save the /etc/inittab file.  Once your box comes back up, you should be given a text-prompt for your username and password.  You can then run startx, or edit your ~/.login file to do this for you (so you don't have to retype it after each login).  That is to say, you can use that workaround method until someone discovers the proper gdm/X configuration to let you just start the computer normally.

Good luck!

---

