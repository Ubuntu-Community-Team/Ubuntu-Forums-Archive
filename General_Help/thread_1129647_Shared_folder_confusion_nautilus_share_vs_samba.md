---
title: "Shared folder confusion: nautilus share vs samba"
date: 2009-04-18
forum: General Help
---

### Post by UranUtan on 2009-04-18
Hi,

Is Nautilus-share the same thing than samba?

I got both working. First started by nautilus right click on of the subfolder in my home folder, slect Share and fill in properties. The only issue is that I must authenticate with my own Ubuntu login/pwd. I prefer that everybody use a common login/pwd dedicated for file shareing.

Then I supposed that I should probably dig into more advance samba settings. After practicing with various tutorials, I got samba working. Then I realize that the two sharing system are different:

- nautilus-share didn't write anything in smb.conf

- samba shared folders don't have the "shared" icon (the little hand) in the folder icon when displayed in nautilus.

Q1. Are they really different and how to make the two compatible with each other?

Q2. Strangely enough, all the samba tutorials I read finished by showing how to access linux shared from Windows machine. They don't cover the following scenarios:

- Accessing Windows folder from a Linux machine
- Accessing samba shared folders from another Linux machine

Is it possible?

Thanks in advance for any help.

---

### Post by Yashiro on 2009-04-18
A1 - The right click created shares are called usershares. 
They use a more simplified setup (config files in /var/lib/samba) and were meant to simplify sharing in general. 
They usually just confuse people.

Shares created in smb.conf are traditional shares and are created by the root/sudo user.
Usershares can  be created by normal users without needing root powers.

I would suggest you use traditional shares as they offer more control and are less prone to permission errors.
You can use the samba control panel to administer them from one place.


A2 - To access a Windows machine just browse the Network in Nautilus like you would browse the network on Windows Explorer. 
Or you can select File -> Connect to Server and enter the details manually.

Once accessed you can just create a bookmark in Nautilus.
This will give you a permanent shortcut in the bookmarks pane on the left.

It's also possible to mount samba shares on bootup so they're permanently mounted, if you so wish.

---

### Post by UranUtan on 2009-04-18
Thank you for your quick and concise answer.

> **Yashiro said:**
> You can use the samba control panel to administer them from one place.

Is it the system-config-samba package in the Synatic Package Manager?


> **Yashiro said:**
> A2 - To access a Windows machine just browse the Network in Nautilus like you would browse the network on Windows Explorer. 
Or you can select File -> Connect to Server and enter the details manually.

Once accessed you can just create a bookmark in Nautilus.
This will give you a permanent shortcut in the bookmarks pane on the left.

Practicing from another Ububtu machine, I see the workgroup name displayed. Clicking on the workgroup I got an error "Unable to mount location, Failed to retrieve share list from server". Don't know what is the cause right now but I'll try to search for a solution.

---

### Post by Yashiro on 2009-04-19
> Is it the system-config-samba package in the Synatic Package Manager?Yes. It seems to work ok, generally.

> Clicking on the workgroup I got an error "Unable to mount location, Failed to retrieve share list from server". Don't know what is the cause right now but I'll try to search for a solution.Usually a permissions problem. As a test try creating a new folder say *sudo mkdir/media/testshare*
Set it's permissions to read/write access for everyone (777) for now. Then share this folder using samba. 
Make sure every PC is on the same workgroup and that workgroup is also the same within smb.conf
Be aware that when you make changes to smb.conf you then need to run *sudo /etc/init.d/samba restart* for the changes to take effect. 

Nautilus is also sometimes slow to pick shares up. So try the manual file menu -> connect to server method.

---

### Post by Cyan_Fire on 2009-10-10
Just wanted to thank you, Yashiro, for the tip about system-config-samba. It's just what I needed and works great.

---

### Post by tg3793 on 2010-11-23
Yashiro I'd also like to thank you. I'm probably just as guilty as thousands of other people for dropping by a newsgroup, getting my answer, and then running away :-) ... 

But occasionally if I see a thread where there was only one person giving thanks for an obviously great answer; I'd like to be that second person to say "Hey, thanks alot for the time you put into helping us newbies out!".

God bless!

---

