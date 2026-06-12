---
title: "Sharing Folders"
date: 2009-01-25
forum: General Help
---

### Post by elkade on 2009-01-25
I am relatively new to linux.  I am attempting to create a home network.  I have 2 desktops running Ubuntu, 1 with WinXP, and a laptop using Ubuntu.

Just tried to share my home folder and this is the message I got:

'net usershare' returned error 255: net usershare add: cannot share path /home as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

Don't know how to get to Admin and make these changes.

I am also struggling with the network setup thing.  Could someone direct me somewhere for some tutorials of some kind?  

Thanks for your help

Larry

---

### Post by Yashiro on 2009-01-25
In terms of security it would be safer to do what the message says.
Only share folders in YOUR home folder, not the /home folder. That is only share /home/elkade/public, for example.

This should work. You may need to reboot after making the first ever share, but it 'should' be ok after that.
Assuming this fails, or you want to unlock everything for shares (not that wise), you can continue with this post.

--- 

First of all make sure all computers are looking for the workgroup named WORKGROUP. This is usually the default anyway.

Back to the warning message. To edit the file that controls shares.
> sudo gedit /etc/samba/smb.conf

Shares created by the Ubuntu GUI are not traditional shares. They're called usershares. 
This is not very clear to users and they often fail to work as users expect.
To allow better access using these shares add these lines to your smb.conf

> # usershares 
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

Save the file and reboot.
You should now be able to make shares of any folders using the gui. You shouldn't need to edit config files anymore.

If you still have problems, you can try using this file as your smb.conf. It allows you to make shares from all folders and give /read/write to everyone.

> 
[http://pastebin.com/m23162516](http://pastebin.com/m23162516)

---

---

