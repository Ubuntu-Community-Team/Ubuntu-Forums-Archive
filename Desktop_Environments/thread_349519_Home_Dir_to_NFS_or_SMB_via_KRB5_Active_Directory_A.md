---
title: "Home Dir to NFS or SMB via KRB5 Active Directory Auth"
date: 2007-01-30
forum: Desktop Environments
---

### Post by Greslore on 2007-01-30
I am hoping someone can steer me in the right direction.

I set up Dapper 6.06 LTS (Kubuntu) to authenticate users via an AD Domain.  That part works great.  A user sits down, uses his or her windows password, and successfully logs into Linux.  I used this for the setup:  [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)  The user logs in, gets a home folder created in /home/DOMAIN/username.  

The next step is to get the linux user's home directory on a pre-existing unix file server.  The file server has both NFS and Samba set up.  Every user already has a directory created for them to store data with permissions set.  IE - users can not browse other user's network data.  I currently have shell scripts on the linux desktops to map a couple of network drives via SMB.  The script simply asks for user name, then calls the samba share to allow users to enter in their windows password.  

What I want to do: User logs in via their AD username.  Their network directory gets mounted as their home automagically.  Users are happy because now their desktop can be the same for any machine they use.   How exactly can I accomplish this?  In the current smb.conf there is a line: template homedir=/home/%D/%U.  If I can somehow mount their network directory, then just have this setting set to their network drive, that viola.  Can I use smbmount or perhaps NFS to do this?  How do I pass either service authentication at user login time before smb.conf gets loaded?  Preferably without asking the user to manually authenticate again.  Or is there a better, easier way to do this?  Any advice, GREATLY appreciated!!  :)

---

### Post by Greslore on 2007-01-31
Still no progress :(.  I tried to use smbmount, but am unsure how to pass authentication at login time to map the home directory.  I cant really use a .win_user_pass file to store the credentials.

Anyone know a good way to do this and perhaps point me to a howto?

---

### Post by cmdln on 2007-06-21
Any luck on this?
Maybe you can use pam_login with autofs ?
Im looking to do this soon so im just poking around.

---

