---
title: "How to share?"
date: 2009-04-21
forum: General Help
---

### Post by mubbashar on 2009-04-21
how can i share a folder on ubunto without using samba when i simple share the folder using right click it give me an erro..

---

### Post by prem1er on 2009-04-21
What error did it give?

---

### Post by DGortze380 on 2009-04-21
> **mubbashar said:**
> how can i share a folder on ubunto without using samba when i simple share the folder using right click it give me an erro..

Need more information.
What exactly are you trying to share?

So far we know, you have a folder, on an Ubuntu system, that you would like to share ...

... with other users?
... over a network?
    ... with other Ubuntu Machines?
    ... with Windows Machines?
    ... with Macs?
... over the internet?
... via snail mail ... ok, maybe not that one ... but you get the idea.

---

### Post by mubbashar on 2009-04-21
how can i share a folder on ubunto without using samba when i simple share the folder using right click it give me an erro..

---

### Post by mubbashar on 2009-04-21
this gave me this error 

'net usershare' returned error 255: net usershare add: cannot share path /media/Software+study/Software/linux/vlc as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.
i want to share with windows and linux os....

---

### Post by mubbashar on 2009-04-21
please tell me...........

---

### Post by Iowan on 2009-04-21
> **mubbashar said:**
> 	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.Is this line already in your smb.conf?  I'm not really familiar with "new Samba" and the "simple share".  From what I've read, you might have better luck defining the share the conventional way in */etc/samba/smb.conf*.

---

### Post by kdla1957 on 2009-06-18
> **Iowan said:**
> Is this line already in your smb.conf?  I'm not really familiar with "new Samba" and the "simple share".  From what I've read, you might have better luck defining the share the conventional way in */etc/samba/smb.conf*.

How do I edit smb.conf to add this line? I'm sure this is a very simple task - just freshly jmping out of Windows comfort zone... :D

Thanks in advance. Kerry

---

### Post by t4thfavor on 2009-06-18
sudo gedit /etc/samba/smb.conf will get you an editor with the file smb.conf in it. 

The error sounds like you don't own the directory. Maybe you could just "sudo chown user:group /Path/To/Directory".

---

### Post by hibliss on 2009-06-18
```
gksudo nautilus
```

Then navigate to the folder you want to share, right click and change the folder sharing permissions.

The issue is that you are trying to share a folder that is owned by root and you don't have the rights to do that as a regular user.

---

