---
title: "Simple way to password-secure my ftp site?"
date: 2006-04-18
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-04-18
I'm looking for a simple way to secure several folders at my ftp site. I've tried some stuff a few weeks ago, but it seemed... less simple than intended.

Is there any *simple* way? Like: 4 steps: 
1) Klick "Add password"
2) Enter usernames
3) Enter passwords
4) Press enter
Something like that?

Doesn't have to be very secure, I got no big secrets there. I just don't want people who use my site to be *too* tempted to read my personal correspondence and stuff.

Thanks

G

---

### Post by hw-tph on 2006-04-19
How to do it depends on what FTP daemon (server) you use. Disable anonymous logins to start with.


Håkan

---

### Post by GabrielWolff on 2006-04-19
[QUOTE=hw-tph]How to do it depends on what FTP daemon (server) you use. Disable anonymous logins to start with.


Håkan[/QUOTE]

Translation needed: I don't know what ftp server I got. I got some space from a Ubuntu user, and I'm using gftp or Nautilus to upload to the site (or delete from it)

Does that help?

G

---

### Post by hw-tph on 2006-04-20
Ahh, I see. I thought you meant you were hosting the server, not the other way around.

There is, as far as I know, no way to simply password protect a directory in FTP from the client side. That has to do with the server configuration, so ask your friend if (s)he can set it up for you.

FTP daemon is the server software that your FTP client (gftp) is talking to. Most have quite exhaustive configuration options. I don't know of any way to password protect a directory (not saying there isn't but - no, I don't find it probable), but you could easily set up different options for different FTP users. You could have anonymous users only have read access to a single directory, system users have access to their home directories and other named users access to the directories and files of the system administrator's choice.


Håkan

---

### Post by GabrielWolff on 2006-04-21
[QUOTE=hw-tph]...but you could easily set up different options for different FTP users. You could have anonymous users only have read access to a single directory, system users have access to their home directories and other named users access to the directories and files of the system administrator's choice.[/QUOTE]

Yes, that's *exactly* what I'm looking for. Could you direct me to a specific software or HOWTO as to how I set that up?

Thanks a lot

G

---

### Post by hw-tph on 2006-04-21
That would be up to the host to set up, and it is dependant on what FTP daemon your friend uses. The documentation for each FTP daemon will usually include a few different examples depending on what you want to do - vsftpd examples can be found [here](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.4/EXAMPLE/).


Håkan

---

