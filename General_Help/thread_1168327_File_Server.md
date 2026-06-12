---
title: "File Server"
date: 2009-05-23
forum: General Help
---

### Post by RedSingularity on 2009-05-23
I want to set up a file server on my ubuntu install that i can access via the internet.  Something to save files to and retrieve from any computer with internet access.  Has anyone done this before that can give me some pointers?  

Thanks

---

### Post by asmoore82 on 2009-05-23
This is extremely easy if Windoze is left out of the equation -
just install ``openssh-server''

This method opens only one port on your Ubuntu box and you have access
to SSH, SCP, SFTP, Apps over SSH/X, and Rsync over SSH all securely and encrypted 8-)

Okay I'll be nicer - if you like all of the above benefits and want to access it from
Windoze as well, you could use PuTTY for SSH and FileZilla for SFTP.

BTW, for easy SFTP access from other Gnome desktops(Linux, BSD's, OpenSolaris),
you can simply "Places -> Connect to Server..." and choose ``SSH'' as "Service Type"
*Doesn't this make windoze systems feel so stoneage?*

---

### Post by Boondoklife on 2009-05-24
Well this would really depend on what type of access you will have on the client computer but here are a couple options.

1) VPN + SAMBA
You could install openvpn or utilize your routers VPN functionality if applicable.
Install samba to permit file sharing.
This setup will allow you to browse the system as if it was on the local lan and it will be encrypted, but will also require a vpn setup on the client.


2) FTP
You could install an ftp server, take your pick as they all do the same thing.
This only requires you to be able to access an ftp application. You can achieve encryption through the server or just tunnel it in with ssh.

3) SCP
You could simply use SCP to transfer files, this only requires an SCP client on the computer.

Hope it helps.

---

### Post by trench.me on 2009-05-24
**[asmoore82]("http://ubuntuforums.org/member.php?u=341737")**'s method is the way to go. 

Basically Ubuntu is already a file-server, you just need to learn the tools to access it (as well as secure it). You'll find loads of [tutorials]("https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto") and [how-to's]("http://principialabs.com/beginning-ssh-on-ubuntu/") about ssh if you [look]("http://google.com").

I'll give you a basic session.

Let's say the user on your Ubuntu install is shadow121. If you wanted to access that account from another system you'd simply open a terminal and type the following:

```
ssh shadow121@shadow121'sIP
```
(You might need to append a port number to the tail of the IP depending on the setup.)

You'll then be prompted for the password. 

(And you'll end up creating a unique passphrase.)

The very first time you do this you'll get a warning that sounds a bit ominous, but it's just warning you that you are about to connect with another system - which always has its pros and cons. 

Once you're in the account you *are* shadow121 and therein have access to all files the user has access to.

Simple as that.

If you need a graphical interface, Nautilus is the way to go. The "Places... Connect to Server" method **[asmoore82]("http://ubuntuforums.org/member.php?u=341737")** was referring to. You can even bookmark it within Nautilus (so it shows up in "Places... Bookmarks"), and even have the system store the password. 

So in every way it becomes just like browsing a local system. Depending on the connection speed of course. 

A side note - as simple as it sounds, if used correctly it is the most secure way of connecting systems. FTP, on the other hand, is the antithesis of secure. Learn ssh and you'll be a happy camper. (As opposed to a sad camper I guess.)

;)

---

### Post by RedSingularity on 2009-05-24
Great.  Thanks for the input everyone.

---

### Post by Aped on 2009-05-24
What's the 'folder path' or whatever supposed to be? A path to specified share set up on the server machine? The path for ubuntu to map the network drive to on your local machine? If the former, how is that set up on the server? If the latter, what are the rules for it (like mounting a drive, do you need to make a /dev/netdrive or something?), and if it's neither of those, what the hell is going on o.O?

As a follow-up, I've been using ssh -X and then 'nautilus &' now, but it's well laggin. Would love to have a proper-style network share worked out, tho this does the trick for the time being, I guess. Can't really even stream music at these rates tho ;)

---

