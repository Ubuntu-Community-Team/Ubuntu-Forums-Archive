---
title: "who are pam and ldap"
date: 2005-12-21
forum: General Help
---

### Post by linrasta on 2005-12-21
(edit)- What is LDAP anyway?  What do LDAP and PAM stand for?
Hello, I am trying to setup a file server and network login and the works, with each user having space on the server drive, mounted, etc, you know the drill(I hope).  Someone told me that what I wanted to use was PAM authentication.  I googled it, and the closest I can come up with is LDAP Authentication Client.  What is this?  Is it related? Does anyone know where I can find more info or a howto on PAM authentication?  And, and for a related question- Is there a way I can mount a zip drive on my ubuntu server to my XP(os) machine?  Thanks, what a great forum.

---

### Post by psoleko on 2005-12-21
Uh Oh, seems you are drowning in acronym soup. LDAP is a type of directory service like Active Directory and Novell Directory Services...I don't think that's what you want to do. PAM stands for pluggable authentication module and basically it let's you authenticate users using whatever kind of authentication you wish, Kerberos and the like. Here's a handy little How-To from out tips and tricks forum for sharing files...
[http://ubuntuforums.org/showthread.php?t=76647&highlight=samba](http://ubuntuforums.org/showthread.php?t=76647&highlight=samba)
You can create a share to the mounted Zip disk under samaba and that should get you going. Hope this helps.

---

### Post by linrasta on 2005-12-21
Thanks for the link.  I learned some things I didn't know.  I have file sharing working fine, but i want my winxp machines require logins(like at a school or work) and when they login, to have their "home" folders mounted, so all of their data is accessible.  Isn't this PAM authentication?  And what is kerberos?  I have read it a million times, and never learned what it is?

---

### Post by psoleko on 2005-12-21
Ouchie..sounds like you want a domain. In which case you will need some sort of directory service, and winbind, and alot of stuff. Most of which is not my area of expertise in Linux..though I could proabably tell you everything on the MS side *sigh* Kerberos is an authentication protocol, PAM is more of a method. So you would authenticate with PAM using whatever protocol. (believe it's Kerberos for domains)

---

