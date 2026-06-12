---
title: "ssh question with no login, no home directory user"
date: 2022-11-25
forum: Desktop Environments
---

### Post by mike430 on 2022-11-25
Howdy Linux Pilgrims!

Setup a no login, no home directory user for purposes of accessing a samba share, but now want this same user to be able to ssh to this machine using no password/ encrypted keys.

My question, do I need to delete this user and setup the same user with login access and with a home directory or is it possible to configure this user to ssh without these functions?

The user does have a user and group owned directory in /mnt/username/ for purposes of the samba and figured I could create a directory in the same path to hold authorized keys.

Thanks - vcandy50

---

### Post by Tadaen_Sylvermane on 2022-11-25
You can give the user a hidden home. /home is the primary location of user files of course. but you can create a user with a different /home path if you choose.

```
dnsmasq:x:108:65534:dnsmasq,,,:/var/lib/misc:/usr/sbin/nologin
jason:x:5004:5004:Jason Gibson,,,:/home/jason:/bin/bash
```



This is an excerpt from my /etc/passwd. Notice the field /home/jason. The same position above for dnsmasq is /var/lib/misc. That directory is the dnsmasq users "home" so to speak as /home/jason is my user's home in the /home directory. I'm not sure of best practices but for a limited user for basic ssh and such you can put it wherever you really want to. It isn't required to be in /home. There might be tools to edit these fields but I personally just manually edit the file if necessary.

> [COLOR=#000000]The user does have a user and group owned directory in /mnt/username/ for purposes of the samba and figured I could create a directory in the same path to hold authorized keys.[/COLOR][COLOR=#000000]

Edit the user in /etc/passwd file as so.

```
sambauser:x:UID:GID:NAME,,,:/mnt/username:/bin/bash
```

As long as the user has proper permissions it should work straight away. If you were to create a passwordless key and ssh-copy-id to this user the .ssh folder would end up in /mnt/username/.ssh[/COLOR]

---

### Post by TheFu on 2022-11-26
> **mike430 said:**
> 
The user does have a user and group owned directory in /mnt/username/ for purposes of the samba and figured I could create a directory in the same path to hold authorized keys.

ssh is picky about the ownership and permissions of the ~/.ssh/ and files inside it.  This means the file system storing those needs to be POSIX, so CIFS/samba or NTFS need not be attempted.  Besides those limitations for security, a HOME/.ssh/ directory can be almost anywhere, including NFS storage.

As stated above, modifying the user's password DB entry is all that is needed, along with ensuring the HOME is available when needed.  It is usually easiest to ensure the HOME is owned by the userid, but that isn't mandated.  The ~/.ssh/ directory must be owned by the userid, however and have 700 permissions.

Editing the password entry can be accomplished in many different ways.  There's a GUI (probably in the Administration menu somewhere), theirs the 'usermod' tool, and there's the sudoedit /etc/passwd method.  The passwd file isn't complex, but if editing it manually, then you'll need to ensure it is "consistent" with other files.  Changing the $HOME is 1 field in 1 file with no other files involved.  Of course, LDAP can also be used for passwds, then the LDAP editing tool would be used. If you didn't specifically setup LDAP, it isn't used.

---

### Post by mike430 on 2022-11-26
So thanks Pilgrims for responding to my questions. 

I am getting close to what I want. To make my quest a little more clear, have a server and 4 clients or family members and myself. I am the only loginable user on the server and have the 3 other members with no home dir/ no login but have access to partitioned attached hard drives with their owned directories. /mnt/user1.hd, /mnt/user2.hd...etc. The original intent was samba which works as planned. 

I am now on to setting up with several users tmux and ssh for some collaborative fun. I want to keep the users with no home directory and no login but have ssh access.

I believe I concluded, with your help, that the server needs loginability, but does not necessarily need a home directory to function with ssh. Could either of you confirm that a login is absolute necessary for ssh to run, or the login is only necessary to setup the authorized key and once this is setup I can turn off their loginability on the server.

Further, I have setup a centralized area to hold the authorized keys on the server in this directory /etc/ssh/%u/authorized_keys. I use the AuthorizedKeysFiles setting in sshd.config 

I am confused by ownership of the authorized_keys in this directory, per the book 'SSH Mastery', they clearly indicate that the authorized_keys needs to be owned by root. When owned by root I get permission denied, but when I change it back to the user it works. 'SSH Academy' on the other hand, makes no mention of the Authorized_Keys being owned by root. 

I also imagine the most efficient and safe way of copying any public keys to the server is by way of 'scp'. 

Thanks for your help and feedback. vcandy50

---

### Post by TheFu on 2022-11-26
> **mike430 said:**
> I am now on to setting up with several users tmux and ssh for some collaborative fun. I want to keep the users with no home directory and no login but have ssh access.

I believe I concluded, with your help, that the server needs loginability, but does not necessarily need a home directory to function with ssh. Could either of you confirm that a login is absolute necessary for ssh to run, or the login is only necessary to setup the authorized key and once this is setup I can turn off their loginability on the server.

ssh doesn't go through the formal login process, so you can lock accounts using normal PAM tools, but ssh will still be possible.  However, I don't believe ssh will be allowed using keys since keys need to be located in $HOME/.ssh/ and the owner of that directory **must** be the userid coming in over ssh.  You'd have to check the ssh book, but what you seek is definitely an edge situation.

> **mike430 said:**
> Further, I have setup a centralized area to hold the authorized keys on the server in this directory /etc/ssh/%u/authorized_keys. I use the AuthorizedKeysFiles setting in sshd.config 
My first thought is that this is a terrible idea.  There are certainly security ramifications in doing that. Individual settings DO NOT BELONG under /etc/.   There are reasons for that, I'm certain.

> **mike430 said:**
> I am confused by ownership of the authorized_keys in this directory, per the book 'SSH Mastery', they clearly indicate that the authorized_keys needs to be owned by root. 

I suspect you are reading a cookbook for an extremely specific situation.

> **mike430 said:**
> When owned by root I get permission denied, but when I change it back to the user it works. 'SSH Academy' on the other hand, makes no mention of the Authorized_Keys being owned by root.  
Use the O'Reiley book and the manpages for the specific commands/settings.  ssh is constantly changing and the manpages on your systems are the best, current, guide.

> **mike430 said:**
> I also imagine the most efficient and safe way of copying any public keys to the server is by way of 'scp'. 
The easiest way is to use ssh-copy-id, but that requires logins be allowed since the password will be used that first time, before you lock the account.  I have passwords allowed only on the same subnet, but other subnets or the internet must use ssh-keys or ssh-certs for authentication.  The sshd_config file has lots of options, including what is allowed based on subnet CIDR or domain.

What's the big deal with setting up HOME directories?  I'm confused.  You can prevent ssh and only allow scp/sftp access, if you like.  You can force a restricted shell, if you like. You can have root be the owner of their HOME, so they cannot create any files/directories and only if they know this, then they can create files/directories under ~/.ssh/.  Setup a tiny quota, if you like or a chroot to some other location.  Perhaps there are better options for the final answer.  What's the point of allowing ssh connections, but not having a HOME?  Do you want them limited to some read-only area?  You could place them into a restricted shell or a shell that runs inside a private firejail; nothing they do will touch storage and they'd only see the HOME (it is configurable).  Lots and lots of options.

---

### Post by TheFu on 2022-11-26
I wrote a long reply that was eaten by the UF software.  Sigh.  

The last sentence was something like this:
What is the real need?  There are lots of options to control where users have access and their HOME can also be controlled.  So, what's the final purpose, so we can provide the known-to-work solutions that almost positively already exist.

Also, I said that you should be using the manpages for ssh and the ssh config files, since everything else that isn't on your system is wrong.

---

### Post by mike430 on 2022-11-27
> **TheFu said:**
> ssh doesn't go through the formal login process, so you can lock accounts using normal PAM tools, but ssh will still be possible.  However, I don't believe ssh will be allowed using keys since keys need to be located in $HOME/.ssh/ and the owner of that directory **must** be the userid coming in over ssh.  You'd have to check the ssh book, but what you seek is definitely an edge situation.

10/4 on this. Currently keys are in /etc/ssh/user/auth_keys and only this is owned by user. Agreed, that this needs to be changed. I also attached an excerpt from the book that describes the setup. Maybe I'm not reading it right??
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291308&stc=1[/IMG]

> **TheFu said:**
> 
My first thought is that this is a terrible idea.  There are certainly security ramifications in doing that. Individual settings DO NOT BELONG under /etc/.   There are reasons for that, I'm certain.

Agreed. I'm not sure where the book is going with this setting. I will replace the location of the auth keys in the user.hd directory. This would  be ok wouldn't it? This directory tree is the only directory on the server they own.

> **TheFu said:**
> 
I suspect you are reading a cookbook for an extremely specific situation.

Yes, the book is ok, I find myself going back to 'SSH Academy'. HTML links makes it easy for navigation and reference.

> **TheFu said:**
> 
Use the O'Reiley book and the manpages for the specific commands/settings.  ssh is constantly changing and the manpages on your systems are the best, current, guide.

I like this!

> **TheFu said:**
> 
The easiest way is to use ssh-copy-id, but that requires logins be allowed since the password will be used that first time, before you lock the account.  I have passwords allowed only on the same subnet, but other subnets or the internet must use ssh-keys or ssh-certs for authentication.  The sshd_config file has lots of options, including what is allowed based on subnet CIDR or domain.

I like this too!

> **TheFu said:**
> 
What's the big deal with setting up HOME directories?  I'm confused.  You can prevent ssh and only allow scp/sftp access, if you like.  You can force a restricted shell, if you like. You can have root be the owner of their HOME, so they cannot create any files/directories and only if they know this, then they can create files/directories under ~/.ssh/.  Setup a tiny quota, if you like or a chroot to some other location.  Perhaps there are better options for the final answer.  What's the point of allowing ssh connections, but not having a HOME?  Do you want them limited to some read-only area?  You could place them into a restricted shell or a shell that runs inside a private firejail; nothing they do will touch storage and they'd only see the HOME (it is configurable).  Lots and lots of options.

Here, at the beginning, you kinda of sound like my wife. But that's ok because I love her. 2 reasons, first, and this would be a typical response that would leave you and my wife scratching your heads. I don't like the way it looks when I hop on the server and I see a half dozen user login names. I just want to see my username on there. Second and more rationally, is or was space constraints. When I originally set these up I didn't want to setup 3 accounts with home directories on the primary drive and having them clog it up with stuff. As I mess with this more I have come to the realization that probably a home directory is preferred as with all the configuration settings it comes with. Further the home directory can be placed anywhere, something I did not know way back when. This is all stuff that I'm starting learn. As well I can be stubborn and since the users already have no home directories I wanted to see how much I can do with this original setup.

---

### Post by TheFu on 2022-11-27
> **mike430 said:**
>  ...

Here, at the beginning, you kinda of sound like my wife. But that's ok because I love her. 2 reasons, first, and this would be a typical response that would leave you and my wife scratching your heads. I don't like the way it looks when I hop on the server and I see a half dozen user login names. I just want to see my username on there. Second and more rationally, is or was space constraints. When I originally set these up I didn't want to setup 3 accounts with home directories on the primary drive and having them clog it up with stuff. As I mess with this more I have come to the realization that probably a home directory is preferred as with all the configuration settings it comes with. Further the home directory can be placed anywhere, something I did not know way back when. This is all stuff that I'm starting learn. As well I can be stubborn and since the users already have no home directories I wanted to see how much I can do with this original setup.

Why are you seeing "half dozen user login names"?  I'm confused again.  Do you mean the GUI login?  A proper login manager let's you hide all the names, so none are shown.
As for space constraints, that's why we have disk quotas per userid.
We can place user HOME directories on any POSIX storage, but if it isn't /home/, then snap package installed programs cannot be used.  Without any HOME, no snaps can be used and a number of other programs will fail because they want to create settings in $HOME/.config/.  In theory, they should gracefully handle that situation, but many, especially Gnome-based tools, will crash.

Seeing what is possible, is fine, if that's your intention.

From the manpage on 20.04 for sshd_config:
```
     AuthorizedKeysFile
             Specifies the file that contains the public keys used for user au&#8208;
             thentication.  The format is described in the AUTHORIZED_KEYS FILE
             FORMAT section of sshd(8).  Arguments to AuthorizedKeysFile accept
             the tokens described in the TOKENS section.  After expansion,
             AuthorizedKeysFile is taken to be an absolute path or one relative
             to the user's home directory.  Multiple files may be listed, sepa&#8208;
             rated by whitespace.  Alternately this option may be set to none
             to skip checking for user keys in files.  The default is
             ".ssh/authorized_keys .ssh/authorized_keys2".

```
You might find this interesting:
[https://www.cyberciti.biz/faq/debian-ubuntu-restricting-ssh-user-session-to-a-directory-chrooted-jail/](https://www.cyberciti.biz/faq/debian-ubuntu-restricting-ssh-user-session-to-a-directory-chrooted-jail/)
These days, I'd probably just spin up a Linux Container for the user and destroy it when done.  After all, if google can do this for each of our individual search requests, we should be able to do the same for a temporary ssh session.  But giving the users a restricted shell running inside a private firejail would be funny too.  Messing with end users can be entertaining.

---

### Post by mike430 on 2022-11-29
> **TheFu said:**
> Why are you seeing "half dozen user login names"?  I'm confused again.  Do you mean the GUI login?  A proper login manager let's you hide all the names, so none are shown.
As for space constraints, that's why we have disk quotas per userid.
We can place user HOME directories on any POSIX storage, but if it isn't /home/, then snap package installed programs cannot be used.  Without any HOME, no snaps can be used and a number of other programs will fail because they want to create settings in $HOME/.config/.  In theory, they should gracefully handle that situation, but many, especially Gnome-based tools, will crash.

I was just being facetious regarding login names on the gui. I have only 4, myself included. 

Thank you for providing me some leads on the possibilities of structuring the server configuring end users and such. I think this requires more reading and research on my part per all these mentioned items...certainly sparks more curiosity. I won't bog you down with more questions until I go through the material thoroughly. Plenty to read. I think I'll start with the chrooted jail link.

Take care Fu, hope to cross paths again. vcandy50

---

