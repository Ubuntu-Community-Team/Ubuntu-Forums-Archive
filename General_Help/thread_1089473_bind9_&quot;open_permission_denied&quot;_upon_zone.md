---
title: "bind9: &quot;open: permission denied&quot; upon zone transfer"
date: 2009-03-07
forum: General Help
---

### Post by JanCeuleers on 2009-03-07
I am posting to a new thread here because an earlier thread on this problem has been archived but did not (in my opinion) contain sufficient detail on the solution.

Problem: when configuring a slave zone in bind9, like so:

```
zone "1.168.192.in-addr.arpa"  { type slave; file "/etc/bind/db.1.168.192"; masters { 192.168.1.5; }; };
```

the zone transfer fails with an error message in syslog such as:

```
Mar  7 11:20:09 via named[7608]: dumping master file: /etc/bind/tmp-uf8eUc6RQK: open: permission denied
```

The reason is that the user the daemon runs as does not have write permissions in /etc/bind. This is intentional and should not be changed. If the daemon is allowed to write in that directory, then any (as yet undiscovered) vulnerabilities in named could be exploited to change your master zone files or your name server configuration files, both of which live there.

The solution I have adopted is to move the slave zone files to a newly created directory, owned by user bind rather than root, in which user bind does have write permissions.

```
# mkdir /etc/bind/slave
# chown bind.bind /etc/bind/slave
# mv /etc/bind/db.1.168.192 /etc/bind/slave
```

Obviously, the zone definition in /etc/bind/named.conf.local needs to be changed to match the new location of the file.

---

### Post by JanCeuleers on 2009-03-07
Also, if you are using AppArmor, it needs to be told to permit named to write to the newly-created directory. This is done by adding the following line to /etc/apparmor.d/usr.sbin.named

```
  /etc/bind/slave/* rw,
```

---

### Post by tomon on 2009-07-08
Thanks. It works perfect. :)

---

### Post by edam on 2009-11-03
I found that just using filenames with no absolute paths for the slave zone files fixed it for me. Like this:

named.conf.local:
```
zone "localnet" {
        type slave;
        file "db.localnet";
        masters { 192.168.0.196; };
};
```

According to /usr/share/doc/bind9/README.Debian.gz, the directory /var/cache/bind is now the working directory for the name server daemon, so if you just specify a filename, then the files are saved there. And /var/cache/bind is already made writeable in /etc/apparmor.d/usr.sbin.named, which would also imply that this is the Debian/Ubuntu "preferred" place to keep them.

---

### Post by tc0nn on 2012-03-29
Actually you can just edit one line, or apply the patchfile I've attached.

Basically change this line:
/etc/bind/** r,
to say
/etc/bind/** rw,

then restart apparmor and bind.

---

