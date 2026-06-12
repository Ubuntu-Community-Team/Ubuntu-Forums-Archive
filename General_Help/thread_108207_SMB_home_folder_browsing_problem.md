---
title: "SMB home folder browsing problem"
date: 2005-12-25
forum: General Help
---

### Post by Kadin2048 on 2005-12-25
Hello, all.

I'm having a problem using SMB to share files between two Linux machines. (I know this is something of an odd choice, but I use SMB to access from Windows machines already, and I want to make sure I'm seeing the same things that the windows users are seeing.)

Here is the setup: one fileserver (named Gnat), running Debian Sarge; one client running Ubuntu Breezy.

The server has smb installed and basically working, most windows users seem to have no problems getting to their home folder. However, when I try to connect to the server from my Ubuntu box in Konqueror, I can get to the root level showing all the shares, in my case "homes" and "television." I can access "television" okay, but when I try to get to "homes," so i can access my own home directory, I get this error: "The file or folder smb://gnat/homes does not exist."

I never get prompted from a login name, and if I try to go directly to my home directory (smb://gnat/homes/kadin/) I get a similar error. I think the problem must be authentication? Basically the server isn't recognizing who I am, so it's not letting me access the right home directory. I've tried restarting the smb daemon on the server already. I'm open for any suggestions anyone might have.

How do I fix the authentication problems?

This is the smb.conf file from the server:
```
# Global parameters
[global]
	workgroup = PCS
	server string =  "Family Fileserver"
	encrypt passwords = True
	security = user
	smb passwd file = /etc/samba/smbpasswd
	local master = Yes
	preferred master = Yes
	os level = 35

[homes]
	browseable = yes
	writable = yes
	comment = Home Directories
	read only = No

[television]
        comment = Recorded TV Shows
        path = /home/television/
        browseable = yes
        public = yes
        read only = yes
        write list = kadin

```

---

### Post by mlomker on 2005-12-26
Have you gone into System Settings under the Sharing icon and then Local Network Browsing?  You can set your default SAMBA username/password there.  

That is what I do and haven't had any problems at work with Windows boxes or SAMBA (I'm an NT Admin by day).

The syntax on the Konqueror line is like this:

smb://domain\username@server/share

---

### Post by Kadin2048 on 2005-12-30
Nope, I hadn't done that. I'll give it a shot and see how it works...

Thanks for the info!

---

