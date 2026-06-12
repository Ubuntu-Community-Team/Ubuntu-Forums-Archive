---
title: "Samba Help"
date: 2006-01-04
forum: General Help
---

### Post by broadbend on 2006-01-04
Hi. I'm new to linux and want to be able to access shares from a windows laptop and share files from my windows partition. 


However while trying to set this up I deleted the directory /etc/samba and now I'm stuck...

I've tried uninstalling samba and installing it again to no avail.:confused:

---

### Post by One Quick Question on 2006-01-04
I'm not expert at how apt-get works, but you shouldn't have to worry about /etc/samba anyway.
The only things in that folder were dhcp.conf, gdbcommands, and smb.conf.
An example of the latter can be found in /usr/share/samba/.
For the other two files, I'm not sure what the default configuration is, but in my not-particularly-special setting, all gdbcommands contains is ```

bt
quit

```
and dhcp.conf is ```

   wins server = eth0:<here be the WINS server IP address>

```

...However, I think all you REALLY have to do to is just configure Samba from KControl and everything will be hunky-dory.  Just be sure to specify that the config file is /etc/samba/smb.conf and it ought to work out.

---

