---
title: "pgp: cannot generate pgp key"
date: 2012-01-30
forum: Desktop Environments
---

### Post by StepNjump on 2012-01-30
hi guys,

If someone could help me, I would appreciate it a lot.
I tried to gpg -kg.. It keeps failing with following error:

gpg: no writable public keyring found: eof
Key generation failed: eof
WARNING: Can't find the right public key-- can't check signature integrity.

Then I tried with pga. Error is:
The GPGME library returned an unexpected error. The error was:
General error
This is probably a bug in GPA
GPA will now try to recover from this error.

I'm starting to wonder is there is corruption in my distro

Natty 32bits
up to date with updates.

Thanks in advance,

Step

---

### Post by StepNjump on 2012-01-30
AT-8:~$ seahorse
** Message: init gpgme version 1.2.0
** Message: could not grab keyboard

(seahorse:2789): Gtk-CRITICAL **: IA__gtk_widget_grab_default: assertion `gtk_widget_get_can_default (widget)' failed

---

### Post by BC59 on 2012-01-30
Did you use those commands?```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys xxxxxxxxx
gpg --export --armor xxxxxxxx | sudo apt-key add -
```

If still you have no result, should be a bug. Better search in Launchpad for it.

---

### Post by StepNjump on 2012-01-30
I think I found something:

Cesar Telmo Oliveira Costa (ctelmo-costa) wrote on 2011-04-22:	 #9
I've just deleted one hidden directory and its contents:
1. you must be in your /home/[your username]
2. rm -r .gnupg
3. try again and all will be OK
3.1. something like that shall be the new contents:
drwx------ 3 ctelmo ctelmo 4096 2011-04-22 17:38 .
drwxr-xr-x 50 ctelmo ctelmo 4096 2011-04-22 17:38 ..
-rw-r--r-- 1 ctelmo ctelmo 0 2011-04-22 17:38 gpa.conf
-rw-r--r-- 1 ctelmo ctelmo 283 2011-04-22 17:38 gpg.conf
drwx------ 2 ctelmo ctelmo 4096 2011-04-22 17:38 private-keys-v1.d
-rw------- 1 ctelmo ctelmo 0 2011-04-22 17:38 pubring.gpg
-rw-r--r-- 1 ctelmo ctelmo 0 2011-04-22 17:38 pubring.kbx
-rw------- 1 ctelmo ctelmo 0 2011-04-22 17:38 secring.gpg
-rw------- 1 ctelmo ctelmo 40 2011-04-22 17:38 trustdb.gpg

source: [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/493473](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/493473)

---

### Post by StepNjump on 2012-01-30
Thanks BC59... it works now after rm -r'ing as show above.

Would you suggest a webpage on how to use my newly created pgp key to encrypt files from the CLI?

Tnx

---

### Post by ruffEdgz on 2012-01-30
I suggest this one from gnupg.org:

[http://www.gnupg.org/gph/en/manual.html](http://www.gnupg.org/gph/en/manual.html)

This should be able to get you started.

---

### Post by StepNjump on 2012-01-30
Thank you very much ruffEdgz!

Pete.

---

### Post by StepNjump on 2012-01-30
Before I close this ticket, in case this might help others:

To encrypt a single file:
gpg -e -r 'name of key' file_to_encrypt

To decrypt a single file:
gpg -d -r 'name of key' file.gpg > filename

(passphrase will be required to decrypt)

-e to encrypt
-d to decrypt

---

