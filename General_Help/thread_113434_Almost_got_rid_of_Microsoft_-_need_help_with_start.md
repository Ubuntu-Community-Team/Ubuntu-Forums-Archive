---
title: "Almost got rid of Microsoft - need help with startup script"
date: 2006-01-06
forum: General Help
---

### Post by zachariah on 2006-01-06
Hello All

Well, the project is nearly done: Kubuntu 5.10 has installed smoothly on our institutional Dell box and at long last the Active Directory login works for any old Windows user. 

Now, the last part of the puzzle:

Every user has a 'My Documents' folder on the server, where all personal files are stored. For Windows systems, AD and group policy takes care of all the links and network drives. BUT for Linux it's proving to be a stumbling block.

Any user can go into Konqueror and type smb://username@server/share and it will then go to the desired folder (after entering password again). But this is not acceptable for a userbase used to Windows and seamless networked folders.

All I need is a startup script that will take the username and password and parse it into a command along the lines of:

'mount //server/share /home/username/My Documents'

...In such a manner that the user won't have to re-enter their credentials. I used SADMS to configure all the PAM and SAMBA files and the program seemed to say it would perform this function, but I couldn't get it to do this. SADMS did not allocate any of the Windows users into groups.

The problem is compounded by the fact that different user groups in the Windows AD have their 'My Docs' folders in different shares. This is not a sticking point however, as I may end up dedicating computers to certain sets of users, but it would be nice if Kubuntu could differentiate the groups and act accordingly. 

Help much appreciated, you will be putting a lot of people onto Linux if this can be made to work!

---

### Post by daller on 2006-01-06
Just to start with, does this command work:

smb://$USER@server/share

???

$USER is a system-wide variable!

I'm not using smb-shares, but it's worth a try!

...BTW: Great title - It got my attention (Any Windows-jumper is a friend of mine!) - It encourages me to try helpin' - It's not that encouraging when people just wanna dualboot :) (Sorry folks, don't flame me for this!)

---

### Post by zachariah on 2006-01-09
Hmm...it half works (in Konqueror). Press enter and it asks for the password again, as it should, but does not pass the $USER variable to the next dialogue, so the username must still be entered again. However, it goes to the correct shared folder after entering the full credentials. So, it uses the variable to correctly find the network path, but not for authentication.

Must be something that PAM can solve...but I need a bit more hand-holding to sort it out I'm afraid! Any ideas?

---

### Post by feathers on 2006-01-09
I found it helpful to use LinNeighborhood to figure out mounting smb shares. It is a graphical frontend for smb-client and shows the commands to you. With this command you could write a simple shell script. There, $USER must work. The problem is, the password still has to be retyped. I don't think there is a practical way out of this. 
Or, users could store their password in a file which is then used the next time. The file permissions need to be 600 but it is still a security risk.

---

### Post by zachariah on 2006-01-18
Update: Further work with SADMS and the problem is solved (practically).

During the 'Install PAM' section of SADMS (always a tense moment), you are asked to provide a server name and share name. The server name is not your local Linux hostname but the name where the remote files are kept. The share name is the network name for the shared folder. 

Although there is an option to use '*' for a username variable, this apparently does not work if it is more than one folder away from the root share...

(ie if your share is \shares and your users files are in \shares\users\username, it won't work, but if they are in \shares\usernames then it will)

...which, for our setup, means I couldn't use a variable. Instead I created a new network share on the Windows server that had network shortcuts to all the other directories inside it, and linked this one to the cifsmount folder. So everyone has a fairly easy way of finding their files once they open their net-home directory inside /home. 

Not amazingly elegant I know, but it works...

---

