---
title: "Samba question"
date: 2009-03-10
forum: General Help
---

### Post by LittleCory on 2009-03-10
I am currently running Kubuntu 8.10.  I had a machine set up with my video and music directories shared using samba, but my drive died and now I am rebuilding it.  

The issue is, I can't for the life of me remember how I set it up.  I know there is a GUI way to do it, but I can't find it.  Going into the folder properties sharing tab it tells me that I need to be authorized to configure file sharing, and when I click the button to configure nothing happens.  So what gives here?  I just can't remember how I did it before.  Thanks in advance.

---

### Post by Token-Ring on 2009-03-10
Go to add/remove programs and at the top change the dialogue to all "available applications" then search Samba. The first or second choice should be the GUI interface for Samba. After you install it will be under System >> Preferences or System >> Administration, I forget which one.

I Wish I could be more exact with the names and locations but my Ubuntu machine is on the fritz. Hope this helps.

-TK

---

### Post by LittleCory on 2009-03-10
I had the packages installed already.  For some reason it doesn't want to let me access the share information from dolphin.  It is in the system menu though.  I must have overlooked it twenty times.  Thanks.

---

### Post by CrusaderAD on 2009-03-10
You could also edit your samba file to manually configure the shares:

```
sudo gedit /etc/samba/smb.conf
```

Just replace gedit with your usual text editor.

---

### Post by mugginz on 2009-04-20
LittleCory, I've just been through all the hassles setting filesharing up myself and have put together a page to explain the gui way of doing this.

Hopefully it's of some help.

[http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/]("http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/")

Mugginz

---

### Post by Wiebelhaus on 2009-04-20
First install samba

```
sudo apt-get install samba
```

With this you will have samba installed on your system, now you need to edit the configuration file which is located at:

```
sudo nautilus 
```

-------nautilus for Gnome or konqueror for kde

Right click and edit

```
/etc/samba/smb.conf
```

simple minimal configuration to allow share files from your Linux server.

 
Copy and paste this section with your customizations at the bottom of the config file.

```
[global]

workgroup = MSHOME

netbios name = UBUNTU_SERVER

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

path = /home/USERNAME IN LOWERCASE

 

read only = No

guest ok = Yes

```
 

***_[COLOR="Red"]Reboot after saving config.[/COLOR]_***
 

workgroup; Lets you specify the windows workgroup

netbios name; Lets you specify the name with your Linux PC will be seen by windows PCs
    
security; specifies the level of security, default is user, but if the users on the windows PCs are not the same as the ones on the Linux PC, you better use share instead
    
auth methods; Possible options include guest (anonymous access), sam (lookups in local list of accounts based on netbios name or domain name), winbind (relay authentication requests for remote users through winbindd), ntdomain (pre-winbindd method of authentication for remote domain users; deprecated in favour of winbind method), trustdomain (authenticate trusted users by contacting the remote DC directly from smbd; deprecated in favour of winbind method)
    
domain master; Lets you configure your PC as a domain master or not, in this case we prefer not, as our goal is only to share files
    
wins support; If you want or not to have wins enabled or not 

Now comes the shares section, the string you put between the [] will be how windows will sees the share, in this case share1

      path; You put here the path you may want to share

      read only; yes or no, depending if you want to permit other users to write on this directories.

      gest ok; It is a boolean field, and will permit or not guest users to access this resource 

For simple sharing that is all that is needed.

Cheers

---

### Post by Wiebelhaus on 2009-04-20
> **mugginz said:**
> LittleCory, I've just been through all the hassles setting filesharing up myself and have put together a page to explain the gui way of doing this.

Hopefully it's of some help.

[http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/]("http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/")

Mugginz

Say buddy , I'll have to disagree , I don't think it's a hassle at all. But that's a great write you made there! thanks for the contribution.

Cheers

---

### Post by Joe on 2009-04-21
> **mugginz said:**
> LittleCory, I've just been through all the hassles setting filesharing up myself and have put together a page to explain the gui way of doing this.

Hopefully it's of some help.

[http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/]("http://mugginix.com/articles/2009/Apr/19/Broken-File-Sharing/")

Mugginz

Thanks for the guide!  I couldn't figure out why nothing would happen when I clicked "configure file sharing" but the command you gave in the guide fixed it.

---

