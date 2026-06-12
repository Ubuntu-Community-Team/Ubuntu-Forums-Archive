---
title: "Accessing server via NX Client and SSH"
date: 2007-12-25
forum: Desktop Environments
---

### Post by jonh001 on 2007-12-25
I have a few questions regarding NX Server & SSH that I hope someone can help with.
I have a small server (running Gutsy Gibbon) with OpenSSH and the latest version of NX Server.
I have generated a new set of SSH keys which I use for both NX and SSH access.
Everything works fine but I would like to fine tune the access.  The way I have it now I can access the server through the Internet using my Windows XP laptop running NX Client and the SSH key.  I can also access the server via Putty also using my SSH key HOWEVER if remove the key I can still get in via the standard username & password - I would like to remove this method of access.

Can I set it up such that SSH access is ONLY via SSH key (no more username & password support) while at the same time maintaining the NX Client access?

Everytime I lock down the Putty access to use the SSH key ONLY, the NX Client access no longer works (I get an authentication failure).

Any help or comments appreciated.

---

### Post by MystaMax on 2007-12-25
Hello & Happy holidays!

I believe the link below is what you're looking for:

[https://help.ubuntu.com/community/AdvancedOpenSSH#head-33f24bb24841060d7f9afb4e4eb5bb2e25d04c42](https://help.ubuntu.com/community/AdvancedOpenSSH#head-33f24bb24841060d7f9afb4e4eb5bb2e25d04c42)

It walks you through disabling plain passwords authentication w/ SSH

Basically, you're going to edit /etc/ssh/sshd_config and change

```

#PasswordAuthentication yes
```to 

```

PasswordAuthentication no

```uncommenting the PasswordAuthentication line, and changing its value from yes to no.

---

### Post by rwillmer on 2007-12-27
That is how you configure the SSH daemon to disallow password authentication.

But how do you get the the NX client to use your SSH key rather than a password?
Is this actually possible?

Rachel

---

### Post by MystaMax on 2007-12-28
Oh, I'm not sure how to do that. But, you can take a look at these links, and see if they help:

[http://www.nomachine.com/ar/view.php?ar_id=AR01C00125](http://www.nomachine.com/ar/view.php?ar_id=AR01C00125)

[http://www.nomachine.com/ar/view.php?ar_id=AR01C00126](http://www.nomachine.com/ar/view.php?ar_id=AR01C00126)

good luck...

---

### Post by Rubix_Kyoob on 2008-03-20
> **rwillmer said:**
> That is how you configure the SSH daemon to disallow password authentication.

But how do you get the the NX client to use your SSH key rather than a password?
Is this actually possible?

I second this question.  Seems like allowing password authentication for NX has the undesirable effect of reducing system security, which is a bit un-cool...

---

