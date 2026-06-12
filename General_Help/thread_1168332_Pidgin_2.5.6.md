---
title: "Pidgin 2.5.6"
date: 2009-05-24
forum: General Help
---

### Post by StormRoBoT2 on 2009-05-24
[FONT=Arial][SIZE=2]**[Pidgin]("http://www.pidgin.im/") 2.5.6**      - Wednesday, 20 May 2009

why ubuntu never update this via "update manager" ?

is it safe to direct download from [/SIZE][/FONT][FONT=Arial][SIZE=2]**[Pidgin]("http://www.pidgin.im/") **site?
[/SIZE][/FONT]

---

### Post by spcwingo on 2009-05-24
> **StormRoBoT2 said:**
> [FONT=Arial][SIZE=2]**[Pidgin]("http://www.pidgin.im/") 2.5.6**      - Wednesday, 20 May 2009

why ubuntu never update this via "update manager" ?

is it safe to direct download from [/SIZE][/FONT][FONT=Arial][SIZE=2]**[Pidgin]("http://www.pidgin.im/") **site?
[/SIZE][/FONT]

You'd be better off just adding the Pidgin ppa repository.  If you need help with that, just post back.

---

### Post by StormRoBoT2 on 2009-05-24
> **spcwingo said:**
> You'd be better off just adding the Pidgin ppa repository.  If you need help with that, just post back.
please help, yes i need some help with it

---

### Post by spcwingo on 2009-05-24
No prob.  Let's get started.  First, start by copying/pasting this into your text editor:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXXu9wEEAM2fOLi65x7hpnmDhTelWDSz+2ktpBuaBizVnVrS5clEVW5BfvQQbqzF1rur
gxTf+0y54s+ZIDOX1OIpiaZK9RYIxWq9KuF2urwv4qK3e0AeWYU6b44YPjgFhQ/LEq0QCTuN
/fKpIenTov9P2O66t9d5cQfiAtTB0NogMLiAjXOBABEBAAG0I0xhdW5jaHBhZCBQUEEgZm9y
IFBpZGdpbiBEZXZlbG9wZXJziEYEEhECAAYFAknOAzkACgkQbfU6uV4fG84AJgCgudiLwQbD
+Kur+VdVc8GVMKu15XYAoKzf06cdX4l+RnfTHJ6hj5TQlY9MiLYEEwECACAFAkl17vcCGwMG
CwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRB/uL7gofGWqIi6A/9jDrYXq2wgFjQkCFGH+Nxd
IbGs1O4OKs+AMe2UiN5YVkQu9XOYoaYaxwNe0WnFJhf4cxPChkWYk16GVMchnDWppVUaUGh4
ojmbY4Gi7VnwC0AiMbtZgnJN9NTZ5W2IhmHJKKkFSZcdbcjNr0YL/8XusbTw4Zeb7214G77z
8qj9/Q==
=CKTU
-----END PGP PUBLIC KEY BLOCK-----

```

Save that as pidgin.gpg in your home directory.  Now copy/paste this command in a terminal:

```
sudo apt-key add ~/pidgin.gpg
```

Now press ALT+F2.  That will pop-up a window.  Enter this command:

```
gksu gedit /etc/apt/sources.list
```

Scroll to the very bottom and add these lines:

```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
```

Of course replace jaunty with your release code name.  Save and exit.  Now open another terminal and input this command:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

You should now be golden.

Edit:  I just checked and the new pidgin release hasn't been uploaded to the ppa yet...it should be there in the next couple of days.  ;)

---

### Post by colau on 2009-05-24
Nice tip.

---

### Post by StormRoBoT2 on 2009-05-24
ok, thanks :)

---

### Post by StormRoBoT2 on 2009-05-24
just wan share something,


[B]Skype API Plugin
[/B][http://eion.robbmob.com/](http://eion.robbmob.com/)

---

### Post by spcwingo on 2009-05-25
For those interested 2.5.6 has been uploaded to the ppa and is working beautifully.

---

