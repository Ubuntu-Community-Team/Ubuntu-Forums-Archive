---
title: "SWAT and root"
date: 2005-10-16
forum: Desktop Environments
---

### Post by triplep on 2005-10-16
I'm sure there is a nice and quick solution for this question:

How do you login as root in SWAT(samba management) in Ubuntu?

bouns Q that no one may answer... how do i restart inetd? killing it was easy ;P

---

### Post by HermanAB on 2005-10-16
Hmm, Swat is a POS - just my 2p worth.  It is easier to edit /etc/samba/smb.conf by hand.  However, if you insist, try 'sudo swat'.

You are probably running xinetd, so try:
# service xinetd restart

You can see what start scripts you have with:
# ls /etc/init.d

Cheers,

Herman

---

### Post by NewbieNik on 2005-10-17
As its a web-interface you need to run Firefox as root, try "sudo firefox" then access swat as before!
And I don't believe its a PoS, I believe it is a fantastic tool to allow people to get used to the smb config if they are new to linux.
As we all would like to see Microsoft phased out, anything that makes Linux more accessible gets a thumbs-up from me!

---

### Post by triplep on 2005-10-17
I took an unsecure step and decided to have inetd spaw demo sessions using swat -a in the config, which works, but when the machine goes live, i may just disable it altogether...

I will try sudo firefox though

---

### Post by hamil on 2005-10-17
If you set the password for root, you will have no trouble at all login in to Swat.

The command:
sudo passwd root
Will set the root password, so you can login to swat as root.
Anyway, thats the way I did it..

After lookin through the wiki, it states taht this is not recommended to do at all, since it could break some of the admin GUI.
If you want to disable the root account again, the command for this is:
sudo passwd -l root

It is more about this tema on this page: [Ubuntu wiki about sudo](https://wiki.ubuntu.com/RootSudo)

Brgds
Lasse

---

