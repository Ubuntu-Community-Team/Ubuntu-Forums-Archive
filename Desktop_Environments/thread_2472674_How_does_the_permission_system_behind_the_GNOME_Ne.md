---
title: "How does the permission system behind the GNOME NetworkManager interface work?"
date: 2022-03-08
forum: Desktop Environments
---

### Post by hlinden on 2022-03-08
So - when I use a default Ubuntu desktop installation, the default user created by the installer can just click on the NetworkManager applet in the top right menu and e.g. modify the existing WiFi connections. I'm trying to understand, how the permission checking that happens at this moment works. How is it determined, that this user may pass new settings to NetworkManager using dbus, I assume and NetworkManager will change a system-connection based on that?

Basically, the reason behind this question is: If I set up a new user source in PAM and NSS, e.g. normal  LDAP or an AD - what else do I need to take care of to offer the "out of the box" user experience to users from that user source?

---

### Post by TheFu on 2022-03-08
Gnome has nothing to do with this.

Standard Unix userids and groups.
Each device has a "file" somewhere on the system which has normal Unix owner, group, permissions.  These control access. By placing different users isn't the appropriate group(s), they can have different access levels.

Unix-like OSes are elegant and simple due to this access control model.

I haven't used network-manager in a long time and barely used it when it was new due to issues, so I don't know which daemons and IPC it uses to control networking.

---

### Post by grahammechanical on 2022-03-08
! am guessing and mostly likely I am wrong, that you are unfamiliar with the way the things are done in the Ubuntu Gnome desktop.

When we install Ubuntu we set up a user with a password. That user will have the power to act as administrator of the system. When we log in we work not as the administrator but as a standard user. We can do many things such as changing WiFi networks. At some point we attempt to do something that requires administrator privileges. A dialog appears requiring authentication. We enter the password we used when we logged in and the operation completes. For the period of that action we were the administrator. Then we revert to being a standard user like before.

If we create a second user with a password that second user logs in as a standard user and can do all the things a standard user can but cannot authenticate actions that only the administrator can authenticate. The second user does not have the correct password.

But, the first user can go to system settings>users and unlock the utility with the password and change the settings to allow the second user and password to also work as administrator.

If you want to know how these things work at the code level, then as advised you need to study Unix permissions.

[https://wiki.ubuntu.com/SecurityPermissions](https://wiki.ubuntu.com/SecurityPermissions)

Regards

---

### Post by TheFu on 2022-03-08
And just to add that what makes a user able to use admin tools is controlled by group membership.  Normal, Unix, groups.  Put a userid into the correct group and they are an admin.  That's how Unix works ... well ... unless some addon is there to provide role-based controls. Ubuntu doesn't do that. When I stopped doing Unix admin work, role-based administration tasks were just beginning to be introduced into Solaris.

---

