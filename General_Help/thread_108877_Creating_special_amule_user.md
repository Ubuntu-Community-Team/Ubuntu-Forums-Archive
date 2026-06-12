---
title: "Creating special amule user"
date: 2005-12-27
forum: General Help
---

### Post by jhoderd on 2005-12-27
Dear fellow "ubunters",

I installed Ubuntu yesterday, and it rocks!  I still must get used
to the sudo system though, and my question is related to it.

I have a few users in my system. I am using the aMule P2P client,
and I want all of them to have access to the same transfers.

I have created a special "amule" user, and my idea was that the
amule daemon amuled would run as this user upon startup, and
then each user could control it via the remote GUI or Web interface.

The problem is: how to configure the system so that:
   - the amule user cannot login via a normal shell
   - any normal user can start programmes as amule,
     without being asked for a password

Thanks in advance for yor help!
Regards,
Jean

---

### Post by schilcha on 2005-12-28
[QUOTE=jhoderd]
   - the amule user cannot login via a normal shell
[/QUOTE]

Edit the user preferences and change the user's shell to /bin/false. The user account will still exist, but you'll be thrown out as soon as you login.

[QUOTE=jhoderd]
   - any normal user can start programmes as amule,
     without being asked for a password
[/QUOTE]

For this you can use sudo. I've never configured sudo, but I know that you can do what you want with it -- check man sudo and man sudoers.

I HOPE, that these two changes do not exclude each other (i.e. one can only make one of the two work, but not both of 'em at the same time...), but I simply don't know...

Good Luck!

---

### Post by sciurus on 2005-12-29
Are you sure they'll need to run amulegui as the same user running amuled?

---

