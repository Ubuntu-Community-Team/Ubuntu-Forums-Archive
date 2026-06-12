---
title: "WinXP --&gt; Ubuntu SAMBA Auth Issue"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Blyth on 2006-07-19
Hey,

Im trying to get away from XP on my server as the hardware seems to be ageing and not keeping up with the streaming videos It currently does.

So to try out linux (first timer = 1 week so far), I have successfully got Ubuntu running on a dual boot config.

I got SAMBA installed and have the key hard drives shared under SMB and have them each named.

I have an extencive firewall to protect the internal networked computers from the net, so I want to remove ALL internal authorisation requests when accessing the internal Linux server from the network. Like what I have been use when the network was all XP machines.

I have used the guide at ubuntuguide.org which hints that by following its procedure that it will openup Ubuntu to open access to the shared drives. [http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29[/URL"]See link -]("URL="http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29")
I have followed this to the letter and no errors appeared in the terminal as I entered it.

Here is the problem -
Ubuntu or Samba still asking for authorisation and even when I enter the Ubuntu admin log/pass it will not accept it and will not allow any access to the Samba shared drives.

Sub Question ---
Is it nessacary to create a Samba log/pass when Samba is installed, or, does Samba look at the Ubuntu log/pass and use that by default?

I did follow the same guide to set a [Samba password]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service") but got this result -

blyth@Machine-Linux:~$ sudo smbpasswd -a system_username
Password:
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user system_username. Does this user exist in the UNIX password database ?
Failed to modify password entry for user system_username
blyth@Machine-Linux:~$

Is this where the problem lay?

Thanks for the help in advance!

---

### Post by ellion on 2006-07-19
Samba is using an own user-system. You can create user with smbpasswd (I think).

Guest authentication should also be possible. I'm not too sure but I think you have to add "guest ok = yes" to the smb.conf in the section with your share

//edit:
yes, you create new samba users with `sudo smbpasswd -a username`. Nevertheless the user has to exist in your linux-usersystem.

To use guest authentication you have to set security to `share` in the authentication section of your smb.conf. Again, not too sure. Just configured samba once and that's a while ago.

---

### Post by Blyth on 2006-07-24
Many thanks for the reply, I found the problem was that as is typlical, I didnt read the instructions carefully enough.

I was entering the wrong line for the samba password!

Doh!

---

