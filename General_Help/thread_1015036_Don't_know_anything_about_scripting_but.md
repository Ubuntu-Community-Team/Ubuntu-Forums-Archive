---
title: "Don't know anything about scripting but"
date: 2008-12-18
forum: General Help
---

### Post by Ms_Angel_D on 2008-12-18
I was wondering if someone could help me, I downloaded and installed Gnome Schedule from the repo's so I could create a recurring task that uploads copies of my tomboy notes to a remote server. 

I click new and select "A Task that launches recurrently" then I get lost, the window ask for some commands I don't have any clue as to what to put there.

So any help on how to accomplish this would be greatly appreciated.

Thanks,
Angel

---

### Post by Titan8990 on 2008-12-18
What do you plan to use to upload the copies? SCP, FTP, RSH (rsync), you have many options and must choose one. I would recommend either rsync or SCP.

---

### Post by Ms_Angel_D on 2008-12-18
Hello Titan,

Sorry guess I should have mentioned that I wanted to use FTP. Basically I have a Web hosting account with plenty of free space, so I wanted to use some of it just backup my documents.

But as I said, when It comes to the scripting and commands part, I'm completely lost :(.

---

### Post by Titan8990 on 2008-12-18
I havn't used FTP much. I actually avoid it at all costs (I think it should die and be referred to as a legacy protocol).

Anyways, I won't be able to tell you exactly what command to use since I have not done it before.

If you open the terminal and do:

man ftp


That will be your start.

---

### Post by gsgleason on 2008-12-18
FTP is not good for schedule sync.  I recommend using rsync though ssh or just scp.  I'm sure your hosted server allows you ssh access.  If the hosted server supports public key authentication, you can create a public/private key pair from your local machine and upload the public key to your hosted server under ~/.ssh/authorized_keys.  This will allow your machine to upload files without a password.  Next, you can set up a cron job in your local machine to do it on a scheduled basis.  Do some googling. Here is a resource I found: [http://myhowtosandprojects.blogspot.com/2008/07/sincronize-folders-with-rsync-using-ssh.html](http://myhowtosandprojects.blogspot.com/2008/07/sincronize-folders-with-rsync-using-ssh.html)

Here is another one: [http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

---

