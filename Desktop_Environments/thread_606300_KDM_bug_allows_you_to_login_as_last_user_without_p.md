---
title: "KDM bug allows you to login as last user without password?"
date: 2007-11-07
forum: Desktop Environments
---

### Post by monstermunch on 2007-11-07
Hi,

I think I found a bug in Kubuntu Gutsy that lets you login as the last user who started a new session from your session without needing their password. Using this trick in a multi-user environment, you can start a new session, wait for someone to log in and log out and then login to their account with no password. This is a huge security issue in my eyes but I've seen no action taken on this bug report. Can anyone else reproduce this on their system? It was in Edgy for me, it was fixed in Feisty but it's back in Gutsy. This is my bug report (just login as another account if you have already created one):

[https://bugs.launchpad.net/ubuntu/edgy/+source/kdebase/+bug/103107](https://bugs.launchpad.net/ubuntu/edgy/+source/kdebase/+bug/103107)
> 
Instructions:
 Use KDM as your login manager and login to KDE.
 Open a terminal.
 Type "sudo adduser bug" and fill in the details to create a new user called "bug".
 Goto K-menu->Switch User->Start New Session.
 The KDM login manager screen should appear. Login as "bug" with your password.
 Logout as bug and switch back to your first session (should happen automatically).
 Goto K-menu->Switch User->Start New Session.

What happens:
 You will be automatically logged into KDE as "bug" without being asked if you wanted to or being asked for the password.

What I expected:
 To be presented with the KDM login screen.

If you wait a couple of minutes before doing the final instruction, the expected behaviour happens. My KDM settings say to automatically log in on X server crash and auto-login my main (not "bug") user.

This seems like a serious security problem to me in an environment where people share machines as it would be easy to let someone login as your new session, wait for them to log out and then login to their account with no password.


---

### Post by monstermunch on 2007-11-09
Does nobody care about this? This looks very serious to me but nobody seems to be bothered by it. :confused:

---

