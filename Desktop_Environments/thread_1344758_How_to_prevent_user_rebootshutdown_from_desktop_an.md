---
title: "How to prevent user reboot/shutdown from desktop and gdm?"
date: 2009-12-03
forum: Desktop Environments
---

### Post by msp3k on 2009-12-03
We're looking at using Ubuntu as our next desktop.  We've been using an older version of Debian for years.  Our environment involves an auto-cross-mounting setup where the user's home area physically resides on the desktop on their desk, but can be automounted to any other computer via NFS.  Because of this, our workstations must remain online 24/7 for important things like nightly backups, email delivery, and, of course, services like NFS and SSH.

Using Karmic, I'm having a devil of a time figuring out how to disable (or at least require admin authentication before allowing) reboot/shutdown/hibernate/suspend buttons.

I've tried configuring GConf's /apps/gdm/simple-greeter/disable_restart_buttons = true for the user gdm, but that didn't work -- neither for gdm nor for the average user.

At the moment I'm trying to figure out PolicyKit.  According to gdm's documentation:[INDENT]GDM may be configured to use PolicyKit to allow the system administrator to control whether the login screen should provide the shutdown and restart buttons on the greeter screen.

These buttons are controlled by the org.freedesktop.consolekit.system.stop-multiple-users and org.freedesktop.consolekit.system.restart-multiple-users actions respectively.  Policy for these actions can be set up using the polkit-gnome-authorization tool, or the polkit-auth command line program.
[/INDENT]That sounds great.  If there's one overruling way to prevent user reboot/shutdown for both gdm and the average user, then I'm all over.  Unfortunately, I can't figure out how it works.

I've tried:
```

        sudo polkit-auth \
            --user gdm \
            --block org.freedesktop.consolekit.system.stop-multiple-users
        sudo polkit-auth \
            --user gdm \
            --block org.freedesktop.consolekit.system.restart-multiple-users

```But to no avail.

Surely someone out there has run into this kind of thing before?

---

### Post by msp3k on 2009-12-03
I have also tried:
```
sudo -u gdm gconftool-2 \
      -t bool \
      -s /apps/gdm/simple-greeter/disable_restart_buttons true

```Without success

---

### Post by msp3k on 2009-12-03
Found a solution!

There's probably a way to do this with the policykit command line tools, but after reading the man pages I still couldn't get anything to work.  What worked for me was to edit the XML files directly as root.

The packages you want to install are: policykit, policykit-gnome

The files you want are:
- For reboot and shutdown:
  /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy

- For hibernate and suspend:
  /usr/share/polkit-1/actions/org.freedesktop.devicekit.power.policy

In both files, change any occurance of "<allow_active>yes</allow_active>" to "<allow_active>auth_admin_keep</allow_active>" and you're on your way.  (In the current version of these files, all occurrances of "<allow_inactive>" settings were already set to "no".  If your version differs then you may need to consider changing those values too.)

If anyone knows enough about how to use the command line tools to do this the "propper" way then I'd love to hear about it.

---

### Post by msp3k on 2009-12-03
According to what I've read about policykit, the following should work.  In fact, the following is taken directly from a script that sets the policy for all machines in an organization:

```
polkit-action --set-defaults-active org.freedesktop.consolekit.system.stop auth_admin
```...But it doesn't work for me.  I get the error message:

```
Cannot find policy file entry for action id 'org.freedesktop.consolekit.system.stop'
```

---

