---
title: "OpenSSH Don't know root password!"
date: 2007-06-22
forum: Desktop Environments
---

### Post by ReapeX on 2007-06-22
Hi,

When trying to establish an ssh connection to an other machine I am prompted to enter the root password for that machine.  The machine is running Windows XP and I typed in all known passwords for that machine.  What password is it looking for?

I followed the instructions on these two sites:
[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)
[http://ubuntu-tutorials.com/2007/04/16/update-securing-synergy-over-the-wire/](http://ubuntu-tutorials.com/2007/04/16/update-securing-synergy-over-the-wire/)

I was trying to get rid of the password prompt and use key authentication but I think I messed something up with the keys files in Ubuntu.  

So yeah, two problems unknown root password and keys on client machine.

Thanks

---

### Post by ReapeX on 2007-06-22
Oh and if I try to login to the windows account directly, I am able to connect just fine
username@ipaddress

But if use this command:
sudo ssh -f -N -L 24800:server:24800 server

Then I am prompted for the root password, after guessing I receive:

'Permission denied (publickey, password).'

I believe my public key is correct for the client machine.

When I type in:
ssh -f -N -L 24800:server:24800 server  (without the sudo command)

I see:
myusername(client)@server_ip_address

I'm confused about that part because my username doesn't exist on the server machine.
Any help would be greatly appreciated because I'm stumped.

---

### Post by Bachstelze on 2007-06-22
Wouldn't that be the password of the Administrator account ?

---

### Post by ReapeX on 2007-06-22
> **HymnToLife said:**
> Wouldn't that be the password of the Administrator account ?

That's what I thought, but I typed in all the passwords for the administrator account.

I did figure out a solution to the password problem though, I typed:
ssh -f -N -L 24800:servername@ipaddress:24800 server@ipaddress

That worked, netstat command (server machine) shows a connection to the client machine.
But it isn't showing not for the port number that I specified.

When I start up the program, the network traffic shows that the two computers are connected but not using but not using SSH.
Does anyone know how to verify netwowrk traffic is being used by the tunnel?

---

