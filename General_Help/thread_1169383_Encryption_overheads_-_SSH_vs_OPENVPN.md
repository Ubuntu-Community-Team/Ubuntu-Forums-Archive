---
title: "Encryption overheads - SSH vs OPENVPN"
date: 2009-05-25
forum: General Help
---

### Post by ecolitan on 2009-05-25
I have to make some large file transfers (~30 Gb) to and from a remote machine and am planning to be using rsync to do them.

By default rsync uses ssh to encrypt the data before it sends it, but I also have the option of making a vpn between the two machines and setting up rsync to send the data via rsh without encryption, over the encrypted vpn tunnel. 

I was wondering if anyone has any experience with determining which method is more efficient and has the lower overhead for sending large amounts of data:
1) sending directly over ssh
2) sending unencrypted data, through the encrypted vpn tunnel.

Thanks!

---

