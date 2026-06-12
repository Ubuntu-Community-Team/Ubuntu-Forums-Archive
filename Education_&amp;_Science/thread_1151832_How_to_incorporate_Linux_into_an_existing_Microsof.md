---
title: "How to incorporate Linux into an existing Microsoft domain on school laptops?"
date: 2009-05-07
forum: Education &amp; Science
---

### Post by Potters Son on 2009-05-07
I'm trying to convince the IT staff at my school to at least consider linux for our school's laptops, which are REALLY SLOW running Windows XP. I just know that these dinosaurs wouldn't take so long just to log on, if only we'd take Windows out of the equation. In addition, I suspect that another reason they're slow is people leaving their files on the laptops, making each machine have to handle ~100 sets of logins.

The way my school's infrastructure is set up is through a domain, meaning that people have to log in with a username and password through our wireless network. I think that it's possible to use Samba to authenticate Linux users, but that would require the laptops to be connected to the network BEFORE they log in. On my laptop, I connect AFTER login. Is there a way to get a laptop to attempt to connect to a wireless network on startup? I imagine that if we migrated to linux, the users would have to be unprivileged, unable to administer networks.

---

### Post by albinootje on 2009-05-07
> **Potters Son said:**
>  Is there a way to get a laptop to attempt to connect to a wireless network on startup?

Instead of using Network Manager you can use a manually edited /etc/network/interfaces for this.

Is the "Windows domain" an old fashioned domain or is it "Active Directory" ?

---

### Post by Potters Son on 2009-05-08
I'm think it's a "windows domain", but I'm not sure.

All I know is, I log on to a school laptop or a lab computer (and I know they aren't thin clients or anything), and my username works. In the domain box it says the initials of the school.

---

### Post by albinootje on 2009-05-08
> **Potters Son said:**
> I'm think it's a "windows domain", but I'm not sure.

All I know is, I log on to a school laptop or a lab computer (and I know they aren't thin clients or anything), and my username works. In the domain box it says the initials of the school.

Are the XP machines slow during the login part, or all the time ?
If they're only slow during the login part, then there's most probably "roaming profiles" in use, which means that data is being copied from the file-server to the client machine. You can prevent a bit of that that slow copying each time by e.g. disabling cache in Firefox, and by storing emails on the imap-based mail-server instead of using "Local Folders" in Thunderbird.

Linux clients in similar situations would use NFS to have a shared /home for the users, which is much much faster to deal with for the login part, but my impression is that in your situation it would not be that easy to use Linux as a client there.

Here you get an idea what to deal with,

For Active Directory on their server :
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[https://help.ubuntu.com/community/LikewiseOpen](https://help.ubuntu.com/community/LikewiseOpen)
[http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain](http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain)
For PDC on their server :
[https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows](https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows))
(Skip to the "client" section).

---

### Post by neu2buntu on 2009-05-08
how about making alive usb of ubuntu 9.04 through unetbootin. and load it up through 1 of the computers to show them how quick it is and also the features...  i dont know much about networking etc but i guess ubuntu will always be faster at connections and logging in even under a large network!!! 
    ununtu is already making the connection for wifi as you log in (check your kernel logs) im not sure when windows does this ie on startup or when logged in.... i was on a windows machine a couple of days ago..... wooow was it slow!!!

---

