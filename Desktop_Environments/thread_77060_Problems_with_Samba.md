---
title: "Problems with Samba"
date: 2005-10-16
forum: Desktop Environments
---

### Post by kwisatz on 2005-10-16
I have my desktop Win 2000 PC and my laptop connected in LAN. 
With Hoary Samba setup was very fast and without problems but upgrading I forgot to copy my smb.conf.
I tried with official How-to and I try with a very simple smb.conf like:

workgroup = Oob
netbios name = VELINO
security = SHARE
[share2]
path = /home/kwisatz
comment = Some random files
read only = yes
guest only = yes

From local I can see the shares but from Windows 2000 I can't see my linux shares...
I have this on my syslog:
Oct 16 13:10:15 localhost smbd[21845]: [2005/10/16 13:10:15, 0] smbd/sesssetup.c:reply_sesssetup_and_X(662)
Oct 16 13:10:15 localhost smbd[21845]:   reply_sesssetup_and_X:  Rejecting attempt at SPNEGO session setup when it was not negoitiated.
Oct 16 13:10:20 localhost smbd[21876]: [2005/10/16 13:10:20, 0] smbd/sesssetup.c:reply_sesssetup_and_X(662)
Oct 16 13:10:20 localhost smbd[21876]:   reply_sesssetup_and_X:  Rejecting attempt at SPNEGO session setup when it was not negoitiated.
Oct 16 13:10:22 localhost smbd[21876]: [2005/10/16 13:10:22, 0] smbd/sesssetup.c:reply_sesssetup_and_X(662)
Oct 16 13:10:22 localhost smbd[21876]:   reply_sesssetup_and_X:  Rejecting attempt at SPNEGO session setup when it was not negoitiated.
Oct 16 13:10:37 localhost smbd[21932]: [2005/10/16 13:10:37, 0] smbd/sesssetup.c:reply_sesssetup_and_X(662)
Oct 16 13:10:37 localhost smbd[21932]:   reply_sesssetup_and_X:  Rejecting attempt at SPNEGO session setup when it was not negoitiated.
Oct 16 13:10:50 localhost smbd[22016]: [2005/10/16 13:10:50, 0] smbd/sesssetup.c:reply_sesssetup_and_X(662)
Oct 16 13:10:50 localhost smbd[22016]:   reply_sesssetup_and_X:  Rejecting attempt at SPNEGO session setup when it was not negoitiated.

A lot of times...
I can't find anything on google, 
anyone could help me?
Thanks in advance,

matteo

---

### Post by lithorus on 2005-10-16
Did you setup the windows user on your Ubuntu box?
Eg. ```
smbpasswd *username*
```
Does the win2k box ask for username/password?

---

### Post by kwisatz on 2005-10-16
If I type:
smbpasswd my_windows_user

I get:
Failed to find entry for user my_windows_user
Failed to modify password entry for user administrator

I need a smbpasswd file? 
And then from Win 2000 I see linux shares but I cannot open them (on syslog: chdir /path/to/share failed) ...I don't know why and from linux I see no shares...
uff...
I have to reconfigure samba package?

---

### Post by HermanAB on 2005-10-16
Windows users must also be Linux users.

Here is a guide that should get you going:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

Cheers,

Herman

---

### Post by kwisatz on 2005-10-16
With Hoary I had different users on windows and linux...
but thank you now it works!!
I still have problems, if I put "guest only = no" I can't login with any user/password. This is my smb.conf:

[global]
workgroup = Oob
netbios name = VELINO
security = SHARE
hosts allow = 127.0.0.1 192.168.1.0/24
hosts deny = 0.0.0.0/0

interfaces = eth0 lo
bind interfaces only = yes
[home]
path = /home/kwisatz
comment = Some random files
read only = yes
guest only = yes
browseable = yes
available = yes

However I suppose it's fair secure...
thank you for helping me...

---

### Post by matw on 2005-10-16
> Windows users must also be Linux users.

Make sure the username spelling is the same on both systems.

Also try
```
sudo smbpasswd -a username
```
The -a option is for adding names to the password file.

I suggest you look at the swat package. I'ts a great way to learn what options are available. Not to mention it's an easy to use administration interface.

---

### Post by HermanAB on 2005-10-16
The usernames must be the same on Windows/Linux, but the passwords may be different.  However, it is better to start off with the same passwords on both systems as well - then when the user changes his password on Windows, Samba will automatically modify the password on Linux to correspond - called something like Unix password tracking in the smb config file.

Anyhoo, look at my debug guide, it shows you how to find and fix the problems.  It is not a setup recipe, it shows you how to debug and fix Samba issues:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

Cheers,

Herman

---

### Post by kwisatz on 2005-10-16
Thank you this link was very useful but I insist on hoary I used DIFFERENT usernames on windows and linux and however everything worked...I am sure!
P.S. I still have problems about viewing windows shares on linux...IF I would have SAME user on win and linux what I have to do? Adding a windows user different from Administrator?

---

### Post by HermanAB on 2005-10-16
About the user name thing: I have never gotten it to work with different user names, though the Samba book is about 2 inches thick and I have to confess that I have not read the whole thing.  I suspect that you could get it to work using aliases.  But the bottom line is that every Windoze user must have an account on the Linux box, so to avoid confusion, I keep them the same.

By viewing Windows shares, I am not sure what you mean.  If you mean that you create a folder on a Windows box, share it and then want to view it from a Linux box, then you have to do a few things:
a. Right click the folder and share it - possibly by dragging it to a shared folder - WinXP GUI is funny in this regard.
b. Run the network wizard, select properties, firewall, advanced properties and Allow File and Printer Sharing.
c. The WORKGROUP on the Windows box must be the same as the WORKGROUP on the Linux box - top of smb.conf.

After changing the above, log out and log in again, to force Windows to re-authenticate against the Linux box.  Also, after changing user settings reload samba on the Linux box with 'service smb restart', then log out/in in Windows again. When debugging, it is important to rule out authentication issues, else you'll go nuts pretty quick.

When all of that is correct, then you can use smbclient to browse the net and the Windows share should show up:
$ smbclient -L //windowsboxip -N

You should also be able to log into the Windows box:
$ smbclient //windowsboxip
and it should ask for user name and password, or
$ smbclient //windowsboxip -uusername%password

If that works, then you can browse the net with Konqueror (Kubuntu required!) using a URL:
smb://username%password@windowsboxip/sharename

Konq should then open the share and you can drag and drop files to another Konq window, even if that window is also logged into another machine, even with a different protocol.  So, you should be able to log into a Windows box using smb:// and in another window log into a Linux machine with fish:// or ftp:// and drag files from the one to the other!

'Hope that helps!

Herman

---

### Post by kwisatz on 2005-10-16
Windows shares are the same from a lot of time. This setting worked with hoary so I suppose that will works the same with breezy.

If I type:
smbclient -L //192.168.1.26 -N
I get:
anonymous login successful
Domain=[OOB] Os=[Windows 5.0] Server=[Windows 2000 Lan Manager]

Sharename      Type       Comment
----------       -----      ---------

Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.26 failed (Called name not present)
session request to 192 failed (Called name not present)

---

### Post by HermanAB on 2005-10-16
To expand a bit:
You have to understand how the server/client idea works.  The machine that wants to share a folder, must run a samba server.  On Linux, this server is called smb and nmb - they go together.  On Windows, the server is called, wait for it, drum roll, server.

You can start/stop the Windows server with the command 'net stop server' and 'net start server'.
You can start/stop the Linux server with the command 'service smb restart'.

Therefore, if you only wish to share a Windows drive with a Linux box, then you only need to run 'server' on the Windows box.  Linux need not run smb.  However the WORKGROUP setting in smb.conf MUST BE CORRECT.  Windows starts the server, as soon as you Enable File and Printer Sharing and drag a folder to the Shared Folder - once this server is running, Windows will always run it at startup - there is no easy way to convince Windows to permanently shut the damn thing up again, short of uninstalling it.

If you wish to share a Linux drive with a Windows box, then you have to run smb and nmb and you don't need to run 'server' on the Windows box, but in all cases, you HAVE to enable File and Printer Sharing in the Windows firewall, else the traffic can't get to the Linux box.

Further, if you are only sharing a Windows drive, then the user names and passwords need not be the same anywhere because you can easily specify them when you connect from the Linux box.

If you are sharing a Linux drive, then it is easier if the user names and passwords are the same on Windows/Linux, since the Windows login method is seriously crippled and Windows users don't like it when they get random login pop-up windows while they are browsing shares.

'Hope this helps!

Herman

---

### Post by matw on 2005-10-16
On my breezy machine I just tried
```
# smbclient -L newton
Password: (I pressed return)
Domain=[NEWTON] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        SharedDocs      Disk
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
Domain=[NEWTON] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```
where NEWTON is the XP machine's name. Kwisatz used an IP address.

---

### Post by HermanAB on 2005-10-16
"Error returning browse list: NT_STATUS_ACCESS_DENIED"
It means your username/password/WORKGROUP is wrong.
The good news is that the request got through the Windows firewall, so at least that is ruled out.

Try something like this to browse:
smbclient -L //odin/music/ -N

or
smbclient -L //odin/music/ -U myusername%mypassword

and this to log in and get a smb> prompt:
smbclient //odin/music -U myusername%mypassword

The smb> prompt works like a FTP client and you can copy and delete files and so on.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by kwisatz on 2005-10-16
Well guys, thanks for so fast answers!
In the first I don't have any firewall on Windows 2000 PC, I usually use my "administrator" user without ANY password. So when I try smbclient -L //IP_OF_WIN2000 -U user administrator
and I press enter when prompt asks me a password I obtain a:
NT_STATUS_LOGON_FAILURE

Workgroup name is the same, OOB on both computer...
However win2000 sees my linux shares!

---

### Post by HermanAB on 2005-10-16
smbclient -L //whatever -U username%password

Don't forget the %...

eg:
smbclient -L //whatever -U administrator%adminpassword

---

### Post by HermanAB on 2005-10-16
BTW, to share folders from windoze, you MUST have PASSWORDS for your users, else it won't work.  The Windoze login routines are rather cripple.

I keep updating my debug guide as we go along - it started out as a simple checklist for my own use.  It now has many more things, that I took for granted, but which new users cannot possibly know.

So have a look again over here:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

Cheers,

Herman

---

### Post by kwisatz on 2005-10-16
Thanks for your help but still I have the same problems...what user I MUST use to login on windows machine? My Windows user? In that case I cannot login using my "administrator" user...
If I use this account to login with smbclient I get a NT_STATUS_ACCESS_DENIED without exceptions...

---

### Post by HermanAB on 2005-10-16
You are logging into the Windows machine, therefore you must log in as a Windows user.  This user may be the administrator or any other user that has access to the shared folder.  However, this user MUST have a Windows password.

If the user doesn't have a password, run Control Panel, User Admin and give the user a password.  Windows doesn't allow remote logins without a password.

---

### Post by kwisatz on 2005-10-17
[QUOTE=HermanAB]
If the user doesn't have a password, run Control Panel, User Admin and give the user a password.  Windows doesn't allow remote logins without a password.[/QUOTE]

My administrator user doesn't have a password, but what do you mean for remote login?

---

### Post by HermanAB on 2005-10-17
The user must have a password else it won't work.

Run Control Panel, User Admin and give the user a password.

---

