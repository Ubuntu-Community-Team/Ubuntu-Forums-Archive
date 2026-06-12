---
title: "help: authentication password for LAN (smb)"
date: 2006-05-14
forum: Desktop Environments
---

### Post by october1917 on 2006-05-14
[QUOTE=Unofficial guide]Ubuntu and Gnome make it easy to access files on a windows network share.

Open the Computer Menu, then click on "Network". You'll see a "windows network" icon, open it. The next window shows all the domains/workgroups found in your network. Inside each domain/workgroup you get all the computers in it (that is, those sharing something !). Double-click on a computer icon to access its shares and files. Could it be easier ?

Before showing a computer's shares, your system may prompt you for a name and password. Fill in the form with the credentials of a valid user for the computer you're connecting to. You may additionally store that password in your keyring for convenience.[/QUOTE]

When i go to Computer-->Network, it opens a widow (authentication required) with the above boxes:

> username: myusername (it is automatically filled)
domain: Mshome (it is also filled)
password:                     (which is empty)

I tryied both the user, and the root password, but it didn't accepted it.
I think it is some password for accecing the other computer (the XP running one). Is there a default password? What have i to type in this box in order to be accepted?

If it helps, i inform you that my computer {**g1annis server (Samba, Ubuntu) (G1annis)**}appears in the workgroup computers of XP, but it seems to be inaccesible, even though i have select shared folder.

---

### Post by october1917 on 2006-05-14
Haven't anyone created in Linux a LAN with a pc running widows?

---

### Post by cgjones on 2006-05-14
Are you trying to access a share on Windows or Ubuntu?

---

### Post by october1917 on 2006-05-14
Thank you my friend, i had started to get disapointed

We have 2 computers. The one [**g1annis server (Ubuntu, Samba) (G1annis)** and the other **nora's pc (Tango)**.

I go to Computer-->Network and appears a new box

it says:
> you must login to access 10.0.0.1
username: myusername (it is automatically filled)
domain: Mshome (it is also filled)
password: (empty)

What must i write to fill the empty box?

The 10.0.0.1 computer seems to be "g1annis server" because "nora's pc" is the 10.0.0.6
But which is the "ipconfig" command for linux, in order to ensure this?

---

### Post by cgjones on 2006-05-14
It's **ifconfig** in Linux.

What shares are set up on Ubuntu? Make sure you are using the username and password of the user on Ubuntu, if they are different then Windows. Have you added the Ubuntu user to the smbpasswd file?

---

### Post by october1917 on 2006-05-14
Allright. I'm 10.0.0.1

the only i have already done is

smbpasswd
and i have put a password there. For example 12345
In the previous box i wrote in the empty field: 12345

and now it appears a new one, but now it says
> you must login to access g1annis@10.0.0.1 domain MSHOME
username: myusername (it is automatically filled)
domain: Mshome (it is also filled)
password: (empty)

About the sheared files, i have just right clicked one folder i created in /home/g1annis called Shared, and  set it as shared.
R we on the right way my friend?

---

### Post by cgjones on 2006-05-14
So you are trying to access a shared folder on a computer running Ubuntu from a computer running Windows? If so, what version of Windows is it?

---

### Post by october1917 on 2006-05-14
> So you are trying to access a shared folder on a computer running Ubuntu from a computer running Windows?No, no. Right now i am in the Ubuntu computer. All i wrote before (everything) is what i see in the Ubuntu pc. It's really strange why it requests password to access the pc which i curently use.  :confused: 

I haven't done anything in the XP-running computer. But i see that the XP computer (nora's pc) can see g1annis, but cannot access it.

---

