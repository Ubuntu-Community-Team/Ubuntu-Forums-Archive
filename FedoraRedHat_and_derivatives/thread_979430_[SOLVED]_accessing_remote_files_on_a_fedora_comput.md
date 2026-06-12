---
title: "[SOLVED] accessing remote files on a fedora computer"
date: 2008-11-11
forum: Fedora/RedHat and derivatives
---

### Post by motoperpetuo on 2008-11-11
i'm trying to access files on my fedora 8 laptop from my linux mint 4.0 desktop through nautilus. here's what i do:

1) choose go|location in nautilus.
2) enter sftp://root@10.55.55.2/root (the ip address being that of the fedora laptop)

i get the error "couldn't display sftp://root@10.55.55.2/root – Access was denied."

i've totally disabled the firewall on the fedora laptop, and i'm able to ping it. also, i'm able to access files on the mint desktop from the fedora laptop by following the two steps above (entering the IP for the mint computer, naturally).

does anyone have any idea why i'm getting this "access denied" error? i'm relatively new to fedora. maybe there's an "allow remote access to files" setting somewhere that i'm not seeing (although i definitely spent a lot of time looking).

---

### Post by igknighted on 2008-11-12
You need a logon name/password.  Try logging in via the CLI (ssh <ipaddress>) and seeing if you can login there.  Also, IIRC Fedora disables ssh by default, so you need to activate the service in fedora (system -> administration -> services)

---

### Post by motoperpetuo on 2008-11-12
> **igknighted said:**
> You need a logon name/password.  Try logging in via the CLI (ssh <ipaddress>) and seeing if you can login there.  Also, IIRC Fedora disables ssh by default, so you need to activate the service in fedora (system -> administration -> services)

thanks for your reply. by "CLI" do you mean "command line interface" or something else?

i'm at work now, but i'll try your suggestion when i get home.

---

### Post by motoperpetuo on 2008-11-12
I tried logging in from the shell and got this:

```

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
98:35:81:d5:ae:69:8f:d7:04:83:0d:ec:a4:3a:35:fd.
Please contact your system administrator.
Add correct host key in /home/mmontgomery/.ssh/known_hosts to get rid of this message.
Offending key in /home/mmontgomery/.ssh/known_hosts:1
RSA host key for 10.66.78.2 has changed and you have requested strict checking.
Host key verification failed.

```

does anyone have any idea how i should proceed?

also, the sshd service appears to be running on my fedora laptop.

---

### Post by snakep on 2008-11-12
I've had this error before.  It is possible that the entry in "known_hosts" for your mint computer has been changed.  Open the .ssh/known_hosts and look for an entry for your desktop.  If it exists, one way to get around this issue is just to remove the entry or perhaps delete the known_hosts file (back it up first).  Then when you try to log in, it will ask you if you want to accept the new host.

---

### Post by motoperpetuo on 2008-11-12
> **snakep said:**
> I've had this error before.  It is possible that the entry in "known_hosts" for your mint computer has been changed.  Open the .ssh/known_hosts and look for an entry for your desktop.  If it exists, one way to get around this issue is just to remove the entry or perhaps delete the known_hosts file (back it up first).  Then when you try to log in, it will ask you if you want to accept the new host.

awesome! renaming known_hosts to known_hosts.old fixed the problem. thanks very, very much.

---

