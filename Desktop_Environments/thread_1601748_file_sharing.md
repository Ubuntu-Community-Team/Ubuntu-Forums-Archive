---
title: "file sharing"
date: 2010-10-20
forum: Desktop Environments
---

### Post by f1vnc on 2010-10-20
Hi Everyone,

Sorry if this is a Newbie question.

I have Ubuntu 10.04 installed. I'm trying out file sharing.

I "right click" on a folder and share it - this works a treat from the XP laptops in the house.

But what's going on? The sharing depends on Samba (if I stop Samba, the sharing stops) - but the action of sharing in this way doesn't make any changes to smb.conf.

What's happening? Is there another way that Samba recognises the shares?

I'm a bit mystified.

Many thanks for any ideas.

F1VNC

---

### Post by Morbius1 on 2010-10-20
Samba has two completely different methods available to share directories:

Classic-shares which define shares in smb.conf. 

Usershares ( or Nautilus-shares ) which defines it's shares in /var/lib/samba/usershares. You are using usershares.

You can see your list of shares and how they are shared in the terminal by issuing the following command:
```
net usershare info
```It's best not to mix and match methods but it can be done if you're careful.

---

### Post by luvshines on 2010-10-20
@Morbius

A question came my mind, does usershares method use anything at all from smb.conf (security, workgroup etc) ?

---

### Post by Morbius1 on 2010-10-20
Yes, in fact usershres won't work without it. And just as you said it depends on smb.conf for workgroup, security, and other options.

If you look at the default smb.conf it has the following parameters set up for usershares specifically:

usershare allow guests
usershare max shares 

The other thing is that you can add parameters to smb.conf to control usershares but because of the way usershares are designed they all work on a global level. Things like "force user" and "hosts allow" come to mind. 

As you may know you can actually use usershare to create a share that is the  equivalent to using "valid users" in classic shares but it can't be done ( that I know of anyway ) using nautilus. It has to be done by CLI or editing the share definition. It's somewhat awkward and if you're going to do that sort of thing you might as well use classic shares and it's GUI's. I haven't played around with that feature enough to know how smb.conf interacts with those special shares.

---

### Post by f1vnc on 2010-10-20
> **Morbius1 said:**
> Samba has two completely different methods available to share directories:

Classic-shares which define shares in smb.conf. 

Usershares ( or Nautilus-shares ) which defines it's shares in /var/lib/samba/usershares. You are using usershares.

You can see your list of shares and how they are shared in the terminal by issuing the following command:
```
net usershare info
```It's best not to mix and match methods but it can be done if you're careful.

That's absolutely brilliant - thank you!

Another area to discover!

Cheers
F1VNC

---

### Post by Kanedagr on 2010-10-20
Hi there!! I installed kubuntu 10.10 yesterday and i can't make samba work. I want to share 2 folders from my pc, so they can be accesed by other PCs in my LAN. In kubuntu 10.04 i was running a gui program called samba and from there i could choose which folders i want to share. In 10.10 when i am running the same app, it asks me for a password. I type in the administrator password and it says that it's wrong. The exact window that appears it says: "Enter the administrative password. The application 'system-config-samba' lets you modify essential parts of your system".

When i try "sudo system-config-samba" from terminal, it displays the above:
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 116, in __init__
    self.samba_user_data = sambaUserData.SambaUserData(self)
  File "/usr/share/system-config-samba/sambaUserData.py", line 46, in __init__
    self.readSmbPasswords()
  File "/usr/share/system-config-samba/sambaUserData.py", line 63, in readSmbPasswords
    raise RuntimeError, (_("You do not have permission to execute %s." % pdbeditcmd))
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.

The samba packages that are installed are: 
Samba 1.2.63, libsamba-hostconfig0 4.0.0~alpha13, libsamba-util-dev 4.0.0~alpha13, libsamba-util0 4.0.0~alpha13, python-samba 4.0.0~alpha13, samba 2:3.5.4, samba-common 2:3.5.4, samba-common-bin 2:3.5.4, samba-ldb-tools 4.0.0~alpha13, samba4 4.0.0~alpha13, samba4-clients 4.0.0~alpha13, samba-common-bin 4.0.0~alpha13, samba4-dev 4.0.0~alpha13.

---

### Post by Morbius1 on 2010-10-20
Although your question has nothing to do with this topic I can tell you you have one big problem:
> The samba packages that are installed are: 
Samba 1.2.63, libsamba-hostconfig0 4.0.0~alpha13, libsamba-util-dev  4.0.0~alpha13, libsamba-util0 4.0.0~alpha13, python-samba 4.0.0~alpha13,  samba 2:3.5.4, samba-common 2:3.5.4, samba-common-bin 2:3.5.4,  samba-ldb-tools 4.0.0~alpha13, samba4 4.0.0~alpha13, samba4-clients  4.0.0~alpha13, samba-common-bin 4.0.0~alpha13, samba4-dev 4.0.0~alpha13.     You've got  two different versions of samba installed and one of them is Samba4. All those "alpha13"'s where trying to tell you not to install them.

I'm not a kde user but I would suggest getting rid of the samba4 stuff. It's not ready to use yet.

---

### Post by Kanedagr on 2010-10-20
Thank you for the quick reply. I removed all alpha13, restarted, but nothing changed. The gui app still asks for an unknown password, and the terminal command gives the exact same response.

---

### Post by Morbius1 on 2010-10-21
I would respectfully suggest you start a separate topic. It's asking you for your sudo password and if it says it's wrong you have bigger problems than samba.

---

### Post by Kanedagr on 2010-10-21
I know the sudo password. And i am entering it everytime the pc starts into kubuntu. So i don't thing that this is a bigger problem. Anyway thanks for your concern. I will start a seperate topic!

---

