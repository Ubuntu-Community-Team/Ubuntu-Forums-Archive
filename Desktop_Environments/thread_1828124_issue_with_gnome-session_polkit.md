---
title: "issue with gnome-session polkit"
date: 2011-08-18
forum: Desktop Environments
---

### Post by glisstech on 2011-08-18
I have started experiencing this issue since updates install on Monday morning 8/15/2011.

When I try to open certain applications...
VirtualBox
LuckyBackup
XBoard
gv
Arora
Xchat
Quassel (IRC)
Skype

My gnome session logs out with no warning.

I get the following errors in the auth.log:

Aug 16 09:57:55 UBUNTU-DT polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session8 (system bus name :1.120, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
Aug 16 09:57:55 UBUNTU-DT gdm-session-worker[3903]: pam_unix(gdm:session): session closed for user greg
Aug 16 09:57:55 UBUNTU-DT gnome-keyring-daemon[3929]: dbus failure unregistering from session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Aug 16 09:57:57 UBUNTU-DT gdm-session-worker[11507]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "greg"
Aug 16 09:58:02 UBUNTU-DT gdm-session-worker[11507]: pam_unix(gdm:session): session opened for user greg by (uid=0)
Aug 16 09:58:02 UBUNTU-DT gdm-session-worker[11507]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Aug 16 09:58:03 UBUNTU-DT polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session10 (system bus name :1.281 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Aug 16 09:58:04 UBUNTU-DT dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.287" (uid=1000 pid=11631 comm="nautilus ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.9" (uid=0 pid=1087 comm="/usr/sbin/console-kit-daemon --no-daemon "))
Aug 16 09:58:13 UBUNTU-DT dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.292" (uid=1000 pid=11840 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.9" (uid=0 pid=1087 comm="/usr/sbin/console-kit-daemon --no-daemon "))
Aug 16 09:58:13 UBUNTU-DT gnome-keyring-daemon[11533]: couldn't allocate secure memory to keep passwords and or keys from being written to the disk

And I am forced to log back in to work on my computer. I filed a bug report in Launchpad...Bug #827724 but have yet to see any response. Does anyone have any suggestions on how to fix this, or at least some workaround so that I can run VirtualBox? I use this alot for testing, and to run Outlook with an exchange connection for my work email. This is killing my ability to be productive, and I dont want to be forced back into using WinJunk.

---

### Post by glisstech on 2011-08-18
If no one has a suggestion on how to fix this, maybe someone can give me a better explanation of what polkitd does for my OS. It seems like it authenticates a service or application against the security settings related to my user login account. I read a thread in another forum, which was talking about ck-session vs dbus, and I am wondering if there is some way I can disable this, and if making my user account function more like a root account similar to some of the other distro's might at least make it so I can use the software that I depend on.

If so...How do I alter my user account to function as a "root" account?
What are the risks other than the obvious ease of damaging the OS if I try to play with system related settings?

---

### Post by glisstech on 2011-08-22
Well, since I didn't get any response to any of my attempts to get help with this. I ended up reinstalling Ubuntu, and will just disable updating the OS for now.

---

