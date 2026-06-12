---
title: "Ubuntu 21.04 Remote Desktop Sharing"
date: 2021-06-16
forum: Desktop Environments
---

### Post by MightyMartian on 2021-06-16
I'm having a bit of an issue with the share desktop feature in 21.04. Just a heads up, this is on a Raspberry Pi 4b.

I'm setting a test unit up as a possible replacement for our current aging classroom lab. One of the things instructors will need is the ability to access user's desktop, keyboards and mice, and sometimes without the student having to consent (currently we use TightVNC on Windows boxes).

In the primary account (with sudoer privileges) this pretty much works every time. However, in the student user, without sudo access, when I go to enter the share desktop password, a keyring password prompt appears, I enter the main account password and can set the password, and it works. However, if I log out and log back in again, the password has disappeared, and while VNC is active, no password will work, and I have to go through the process of entering the sudo-enabled account's password in keyring, then storing the password. In other words the share desktop password is not persistent between log ins.

One possible caveat is that I have the student user set with no password. Could this be the issue?

---

### Post by TheFu on 2021-06-17
21.04 support ends in December. Do you really want to bother with a non-LTS release?
Everyone on 21.04 must move to 21.10 between late-Oct and January. There's no choice - unless being unsupported is acceptable.

Would much rather see a fresh deployment begin with 20.04 - which has standard support until 2025 April. That's the magic of LTS releases.  Running a few test systems on 21.04 --> 21.10 --> 22.04 is fine, but not a full classroom deployment, IMHO. 

I can't help with VNC. We used it for a few months, but it was slow and had terrible security. It is against policy and has been for about a decade. Sorry.  If you do use VNC, always set it up for a localhost-only connection. Never allow connections over any LAN.  This forces a tunnel into the system to be used before VNC/RDP can be used.

If using r-pi as dumb terminals, perhaps using a more secure and faster solution like **x2go** would make sense?  x2go only allows connections over ssh, which is part of the NX protocol standard. Normal ssh works and you can lock down the ssh access to only allow x2go, if that is your need (though I don't see much point).  x2go has a shared, view-only, mode. It also supports a full desktop ... well ... for all desktops except the bloated Gnome3.  Plus, x2go feels 2-3x faster than any VNC/RDP I've seen on Linux - local or from another continent.  x2go clients exist for linux, OSX and Windows.  I think there's an Android client too, but I've never tried it.  I know the Windows and Linux clients are solid - like connect for 30 days at a time and it keeps working.  Plus, it is possible to reconnect to a running GUI session like screen or tmux support.  
Multiple, concurrent client connections are supported.  At my small company, we'd have 5 people connected to the same "desktop server" remotely and would have all the normal, expected, Unix methods of file sharing, working together, while having separate HOMEs as expected.
All authentication is handled via ssh, so you could pre-setup ssh-keys from clients to allow access by individual students without any password hassles, if you like.  Just be certain that they do not share the same login usernames.  Setting up ssh-keys is 2 commands, when you know what to do.  You could have a different username tied to each client workstation/r-pi, and only allow connections from that r-pi to use that specific ssh-key. That's not hard.  Setting all this up by a knowledgeable admin person means not having to run around to different systems.  Just get a setup script working for 1 client keeping the username/hostname as a parameter, then doing the same across 5 - 50,000 systems isn't hard.  

Throw in a little Ansible and redoing everything weekly or each quarter/semester will be 1 command from 1 system.  

Forget the keyring.  I've never used it. It isn't needed and just gets in the way. It isn't like students should ever have sudo anyways.

---

