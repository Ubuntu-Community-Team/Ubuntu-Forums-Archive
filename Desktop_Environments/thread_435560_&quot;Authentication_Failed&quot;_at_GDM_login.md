---
title: "&quot;Authentication Failed&quot; at GDM login"
date: 2007-05-07
forum: Desktop Environments
---

### Post by paulrobert_a on 2007-05-07
I've had this problem for some time now, ever since I upgraded my laptop from dapper to feisty.

I start the laptop, load up Ubuntu and get to the GDM Login, I type in my credentials (which are correct), however 9 times out of 10, I'll get an "Authentication Failed" message and at times  it doesn't matter how often I restart, I get the same error message.  I know this has something to do with my profile as I have created a new user account and manage to logon fine every time. 

I've also tried :-

[LIST]
[*]Removing /etc/pam.d/gdm
[*]Changing /etc/X11/Xwrapper.config allowed_users from console to anybody 
(I must note here, my user account only ever logs on when allowed_users is set to anybody, except for my new user account which just works)
[*]Checking permission settings on .ICEauthority & .Xauthority
[*]Reinstalled libpam0g, libpam-modules, libpam-runtime
[/LIST]

I don't know if this is related or not, when I logout the screen goes blank, and the only way to do anything is power down and boot up again.

Hardware : Acer Aspire 5102, Turion TL-50 (X2 1.6Ghz), 1 GB RAM, 100GB HDD (Dual boot, XP 25GB, Feisty 70GB), ATI Xpress 1100 (fglrx enabled)
Software : Ubuntu 7.04 (upgrade from dapper via edgy), fglrx, pam_keyring

Any suggestions would be much appreciated. TIA!

---

### Post by paulrobert_a on 2007-05-13
Has no one, got anything on this? :(

---

### Post by paulrobert_a on 2007-06-13
I was really wanting to nail this problem, but I've exhausted everything I could do :(

The questiest way round the above problem is to create a new user and replace the new profile with the old user profile.

login as root (superuser) under recovery mode
create a new user > useradd newperson
create password for new user > passwd newperson
change to home directory > cd /home
delete or backup new user profile > rm -r newperson OR >  mv -r newperson newperson.backup
move or copy your profile to the new user > mv -r -p oldperson newperson OR > cp -r -p oldperson newperson

I am sure if you login via recovery mode you'll not need to use sudo, however if you receive any errors it's probably a permission problem, just affix sudo to the beginning.  This was a couple of weeks back that I actually did this so forgive me if it isn't complete, obviously use at your own risk.

---

### Post by glennric on 2007-09-19
Did you ever figure this out?  I just began to have this problem today.

---

### Post by fiatguy85 on 2007-10-22
Try this:

[http://ubuntuforums.org/showpost.php?p=3605925&postcount=4](http://ubuntuforums.org/showpost.php?p=3605925&postcount=4)

---

