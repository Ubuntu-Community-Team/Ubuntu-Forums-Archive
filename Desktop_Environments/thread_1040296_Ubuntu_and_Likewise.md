---
title: "Ubuntu and Likewise"
date: 2009-01-15
forum: Desktop Environments
---

### Post by jcagle on 2009-01-15
Im having some issues regarding AD authentication.

I have the PC running Ubuntu 8.10, it has likewise installed and is working great except for one problem.

We have currently two domains. One is called FS and one is called PIONEER. I joined the PC to FS, and can authenticate to FS perfectly (using FS\user at login), but when trying to Authenticate to PIONEER (using PIONEER\user at login) it just sits at the blank background and doesnt load the desktop at all.

What am I missing? Is there an conf file i need to edit?

---

### Post by jcagle on 2009-01-16
Here is output of my auth.log when I try to log in using the PIONEER\Jpionner login

Jan 16 10:39:21 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:auth): Received UPN of: [email]JPioneer@PIONEER.DEW.TWU[/email] [email]JPioneer@PIONEER.DEW.TWU[/email]
Jan 16 10:39:21 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:account): PAM config: global:krb5_ccache_type ‘FILE’
Jan 16 10:39:21 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:account): No membership check being enforced
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:account): Returning 0 for user “PIONEER\jpioneer”
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:account): user ‘PIONEER\jpioneer’ granted access
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:account): homedir is /home/PIONEER/jpioneer
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:setcred): PAM config: global:krb5_ccache_type ‘FILE’
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:setcred): homedir is /home/PIONEER/jpioneer
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:session): PAM config: global:krb5_ccache_type ‘FILE’
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:session): homedir is /home/PIONEER/jpioneer
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:session): Looking up name ‘PIONEER\jpioneer’
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:session): Looking up SID ‘S-1-5-21-261972655-639895445-1814836861-45692’
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_unix(gdm:session): session opened for user PIONEER\jpioneer by (uid=0)
Jan 16 10:39:22 ubuntu504132 gdm[5089]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 16 10:39:22 ubuntu504132 gdm[5089]: gnome-keyring-daemon: couldn’t lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.
Jan 16 10:39:22 ubuntu504132 gdm[5089]: )gnome-keyring-daemon: couldn’t lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.
Jan 16 10:39:22 ubuntu504132 gdm[5089]: )gnome-keyring-daemon: couldn’t lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.
Jan 16 10:39:22 ubuntu504132 gdm[5089]: )
Jan 16 10:39:51 ubuntu504132 login[5362]: pam_lwidentity(login:auth): PAM config: global:krb5_ccache_type ‘FILE’
Jan 16 10:39:51 ubuntu504132 login[5362]: pam_lwidentity(login:auth): failed to get GP info
Jan 16 10:39:51 ubuntu504132 login[5362]: pam_lwidentity(login:auth): getting password (0x00000000)
Jan 16 10:40:02 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:session): PAM config: global:krb5_ccache_type ‘FILE’
Jan 16 10:40:02 ubuntu504132 gdm[5089]: pam_unix(gdm:session): session closed for user PIONEER\jpioneer
Jan 16 10:40:02 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:setcred): PAM config: global:krb5_ccache_type ‘FILE’
Jan 16 10:40:02 ubuntu504132 gdm[5089]: pam_lwidentity(gdm:setcred): PAM config: global:krb5_ccache_type ‘FILE’

---

### Post by jcagle on 2009-01-16
A quick update.

I am able to get in using the failsafe terminal, but upon logon it gives me:

id:cannot find name for group ID ##########
id:cannot find name for group ID ############

---

### Post by tepo on 2009-01-17
I had the same pam-errors when using likewise-open on Ubuntu 8.10 and solved it by removing likewise-open and the gui from synaptics (using remove all). I downloaded the version _5_ installer of likewise_open from their website.

After installing the upgrade, do not use lwiinfo (as in "lwiinfo -p") anymore in the terminal, as ubuntu then tries to re-install the previous version of likewise-open. In version 5, lwiinfo and wbinfo are replaced by lsass. Refer to the version 5 document on the likewise site.

Solved it all, hope it works for you as well

---

