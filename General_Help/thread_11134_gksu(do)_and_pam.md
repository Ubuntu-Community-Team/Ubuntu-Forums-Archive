---
title: "gksu(do) and pam"
date: 2005-01-14
forum: General Help
---

### Post by nocturn on 2005-01-14
Does gksu(do) properly support PAM?

I'm having trouble pointing it to pam_krb5 (what I'm using for authentication).
I changed /etc/pam.d/sudo to this end, and sudo itself prompts me correctly for a kerberos password.

But gksu(do) just hangs, no errors, no password prompt.  I can see the process with ps and kill it.

Does anyone use this (for example with LDAP)?

---

### Post by nocturn on 2005-05-09
Bump, this does not work in Hoary either...

# Tue May 10 10:26:40 CEST 2005 - Filed a bugreport
[https://bugzilla.ubuntu.com/show_bug.cgi?id=10578](https://bugzilla.ubuntu.com/show_bug.cgi?id=10578)

---

### Post by PoochieReds on 2005-05-14
The problem seems to be with either pam_krb5 or sudo. gksudo runs:

/usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- command

When using pam_krb5, it seems that the '-p' option is ignored and the standard prompt is presented. Since the dialog is expecting to see GNOME_SUDO_PASS come across, it just hangs waiting for it.

Probably best to start with sudo and see what the '-p' actually does...

---

### Post by PoochieReds on 2005-05-15
sudo apparently only respects the '-p' if the prompt from the pam module matches the standard format:

/* Only override PAM prompt if it matches /^Password: ?/ */

The best way to fix this might be to add an option to pam_krb5 that changes that prompt to match the standard above (or changes it to something arbitrary).

---

### Post by PoochieReds on 2005-05-15
Ok fixed it by patching sudo such that it _does_ override the pam prompt if -p or $SUDO_PROMPT is specified. This seems like it should be correct behavior and fixes the problem on my box. I'm new to ubuntu, so I need to figure out how best to submit the patch, but FWIW, here it is:

--- ./auth/pam.c.orig   2005-05-15 09:08:15.923873776 -0400
+++ ./auth/pam.c        2005-05-15 09:08:19.003405616 -0400
@@ -226,8 +226,8 @@
                SET(flags, TGP_ECHO);
            case PAM_PROMPT_ECHO_OFF:
                /* Only override PAM prompt if it matches /^Password: ?/ */
-               if (strncmp(pm->msg, "Password:", 9) || (pm->msg[9] != '\0'
-                   && (pm->msg[9] != ' ' || pm->msg[10] != '\0')))
+               if (!user_prompt && (strncmp(pm->msg, "Password:", 9) || (pm->msg[9] != '\0'
+                   && (pm->msg[9] != ' ' || pm->msg[10] != '\0'))))
                    p = pm->msg;
                /* Read the password. */
                pass = tgetpass(p, def_passwd_timeout * 60, flags);

---

### Post by PoochieReds on 2005-05-15
This is BZ#8774. I uploaded a revised version of this patch there.

---

### Post by nocturn on 2005-05-18
Thanks!!!

---

