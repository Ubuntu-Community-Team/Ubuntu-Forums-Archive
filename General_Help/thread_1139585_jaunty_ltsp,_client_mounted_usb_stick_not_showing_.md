---
title: "jaunty ltsp, client mounted usb stick not showing up on servers"
date: 2009-04-27
forum: General Help
---

### Post by slashdotfx on 2009-04-27
Hi,

I'm using jaunty LTSP,
everytime I plug usb stick onto the client (after client bootup),
it detected ok (via dmesg), but whenever 
I look at the server (from mount), it didn't showed up,
I already set LOCALDEV=True, installed ltspfs on server,
add user on fuser group, and following ubuntu wiki
on debugging localdev, on the last step, the ssh
connection (via ldm socket) is hanging, this is the output of
the ssh command

root@w6:~# ssh -S /var/run/ldm_socket_3629_192.168.0.1 id -vvv
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug3: ssh_msg_send: type 2
debug3: ssh_msg_recv entering

but...if I plug the usb stick before powering on the client,
up until the client is booted, it showed up on the server,
but still the ldm_socket is not reusable, as it should be,

root@w6:~# ssh -vvv -S /var/run/ldm_socket_3780_192.168.0.1 w6@192.168.0.1 id
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug3: ssh_msg_send: type 2
debug3: ssh_msg_recv entering

still hanging, if I plugged off the usb stick it not unmounted
automatically.

any hint would be appreciated. thanks.

---

