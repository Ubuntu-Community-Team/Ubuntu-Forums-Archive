---
title: "Amarok Plugin Prob"
date: 2006-09-06
forum: Desktop Environments
---

### Post by mattmac24 on 2006-09-06
Hey, im not sure where to post this, but if i post here i figure somebody will tell me where it actually should be.

My error is that when i run the amarok script "httpremote_amarok" i get the following error:
HTTP::Daemon: Permission denied ...propagated at /home/matt/.kde/share/apps/amarok/scripts/httpremote_amarok/httpremote_amarok.pl line 134.

This error does not happen when i run amarok as root. So i gifured it was  a permissions thing so i have been randomly trying to set the permissions of files to full acces to everybody.
I have been doing this mainly in the opt/ActivePerl-5.8 Dir.

I had alot of trouble with dependancies before this but now i ave correctly installed all of them i think (as it works when running under root).

Does anybody know what file/folder i need to fix the permissions on or what else i need to do to fix this.

Thanks,

Matt

---

### Post by mattmac24 on 2006-09-06
Bump....if anybody has any other suggestions as to where i should post this problem then please help me out and tell me.

Thx, Matt

---

### Post by mattmac24 on 2006-09-07
ok i guess ill try and find some amarok forums to post this problem too as nobody else seems to be having this problem or knows how to fix it.

Matt

---

### Post by mattmac24 on 2006-09-08
and if is helps here are the lines around line 134:

```
# Create HTTP server.
# The option ReuseAddr is used to allow dangling tcp connections (in TIME_WAIT
# state) to be reused immediatly.
--->> Line 134 --->> my $d = HTTP::Daemon->new(
  LocalPort => $config{'tcp_port'},
  ReuseAddr => 1
) || die;
print "Please contact me at: <URL:", $d->url, "httpremote>\n" if $verbose;
```

Thanks, matt

---

