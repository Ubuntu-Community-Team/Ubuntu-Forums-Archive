---
title: "RDP connection errors (from xrdp.log)"
date: 2024-11-27
forum: Desktop Environments
---

### Post by matt-rw on 2024-11-27
Hi All,

I have a miniPC running 24.04 that I am now running headless and I want to be able to run a remote desktop on my laptop running 24.04.

I have installed and enabled xrdp on the miniPC.    When I bring up the Connections app does prompt for username and password, but the connection fails.   Below is the output of /var/log/xrdp.log on my miniPC.   Any ideas where what the source of the error could be? 

```
root# id xrdp
uid=124(xrdp) gid=126(xrdp) groups=126(xrdp),106(ssl-cert)
```

```
20241127-06:42:39] [INFO ] Socket 12: AF_INET6 connection received from ::ffff:192.168.2.155 port 53672
[20241127-06:42:39] [INFO ] Using default X.509 certificate: /etc/xrdp/cert.pem
[20241127-06:42:39] [INFO ] Using default X.509 key file: /etc/xrdp/key.pem
[20241127-06:42:39] [INFO ] Security protocol: configured [SSL|RDP], requested [SSL|HYBRID|RDP], selected [SSL]
[20241127-06:43:00] [ERROR] SSL_accept: Failure in SSL library (protocol error?)
[20241127-06:43:00] [ERROR] SSL: error:0A000126:SSL routines::unexpected eof while reading
[20241127-06:43:00] [ERROR] trans_set_tls_mode: ssl_tls_accept failed
[20241127-06:43:00] [ERROR] xrdp_sec_incoming: trans_set_tls_mode failed
[20241127-06:43:00] [ERROR] xrdp_rdp_incoming: xrdp_sec_incoming failed
[20241127-06:43:00] [ERROR] xrdp_process_main_loop: libxrdp_process_incoming failed
[20241127-06:43:00] [ERROR] xrdp_iso_send: trans_write_copy_s failed
[20241127-06:43:00] [ERROR] Sending [ITU T.125] DisconnectProviderUltimatum failed
```

Also, /etc/xdrp/{cert,key}.pem link to /etc/ssl/certs/ssl-cert-snakeoil.{pem,key}.

---

