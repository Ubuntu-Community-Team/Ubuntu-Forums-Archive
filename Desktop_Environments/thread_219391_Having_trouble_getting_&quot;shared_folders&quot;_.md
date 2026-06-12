---
title: "Having trouble getting &quot;shared folders&quot; to work"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Luggy on 2006-07-19
So I was playing around with the Shared Folders application ( from System/Administration ) and I was having trouble getting it to be recognised by others ( Window users ) on the network.

I have a folder setup to share with smb, specified a hostname and workgroup. The only thing I was confused with was the WINS server options. I set it to 'do not use WINS server' and 'this is a WINS server' but other users on the network could not see me.

Can anyone give me any help?

---

### Post by scxtt on 2006-07-19
can they just 'not see you' or are they getting errors? -- sometimes it takes a 'while' for window's samba to pickup on new hosts, even if they're windows too ... my suggestion would be to make a 'direct connection' via samba using the IP address of your ubuntu box instead of just relying on the 'view network computers' ...

if your share in ubuntu (IP address, 192.168.1.100) is called **ubuntu_share**, when in windows do a "map network drive" and enter:

192.168.1.100\ubuntu_share

---

### Post by Luggy on 2006-07-19
I think the problem might have been that shared-admin was not restarting samba after I had re-configured it. I restarted my computer ( which restarted the deamon ) and my buddy could see the proper workgroup and host.

My problem right now is that my buddy cannot browse the folders that I have set to share using shared-admin.

---

### Post by scxtt on 2006-07-19
try running **smbpasswd -a $username** to allow someone to view the share ...

---

### Post by Luggy on 2006-07-19
Yeah, I'm pretty sure my problems are now just Samaba related and I should be able to fix them easily on my own.

Kinda lame how shared-admin cannot set this stuff up on its own.](*,)

---

