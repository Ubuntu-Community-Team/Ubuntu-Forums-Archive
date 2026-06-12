---
title: "Requesting help re-enabling GDM"
date: 2005-05-02
forum: Desktop Environments
---

### Post by Svenn on 2005-05-02
As a relative newcomer to Linux and even newer to Ubuntu I find it humbling that I have to ask seemingly the simplist things for example I recently was wanting to try a few configuration tools for Xorg however I needed to stop X and prevent it from restarting itself. So as indicated earlier in the forums I 

/etc/init.d/sudo gdm stop

-then-

update-rc.d -f gdm remove

and low and behold I was able to prevent X from restarting once killed. I was able to run through the X configuration utilities. However now I would like to return to a graphical login but foolishly I cant figure out how to re-enable X automatically so I may have gdm login once again. 

~Svenn

---

### Post by Xerampelinae on 2005-05-02
[QUOTE=Svenn]As a relative newcomer to Linux and even newer to Ubuntu I find it humbling that I have to ask seemingly the simplist things for example I recently was wanting to try a few configuration tools for Xorg however I needed to stop X and prevent it from restarting itself. So as indicated earlier in the forums I 

/etc/init.d/sudo gdm stop

-then-

update-rc.d -f gdm remove

and low and behold I was able to prevent X from restarting once killed. I was able to run through the X configuration utilities. However now I would like to return to a graphical login but foolishly I cant figure out how to re-enable X automatically so I may have gdm login once again. 

~Svenn[/QUOTE]
 sudo /etc/init.d/gdm start

Starts gdm until next reboot (similarly giving stop would only stop it until next reboot)

update-rc.d gdm defaults

Adds gdm to the list of things to be started at boot.  Similarly, your command above would only remove it from being started at boot, it wouldn't stop it for the current session.

---

### Post by Svenn on 2005-05-02
Thanks, I new how to start it once again just didn't know the syntax  to add it back to rc.d.:wink:  I knew it was something terribly simple I guess I just wasn't reading the man/info correctly. While I am learning as fast as I can often times its the small things that are the most frustrating.

Once again Xerampelinae I thank you for helping me :)


~Svenn

---

