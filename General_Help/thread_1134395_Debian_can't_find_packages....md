---
title: "Debian can't find packages..."
date: 2009-04-23
forum: General Help
---

### Post by PhoHammer on 2009-04-23
Hello, I realize I'm a bit off-topic here on the ubuntu forums, but your guys are pretty
active here and I think maybe you can help.

I just installed Debian Squeeze from an amd64 netinst  and expected to be able to 
download my desktop environment and such during the install.

Well, things didn't go so well and now I've got an install with no desktop.

I'm connected via ethernet that will ping google successfully, but I can't apt-get
install anything

apt-get install gnome gets me "E: couldn't find package gnome"

Any thoughts?

---

### Post by Tim Sharitt on 2009-04-23
Did you run 

```
apt-get update
```

before trying to install?

---

### Post by PhoHammer on 2009-04-23
Yes, I ran that and it says:


"Err [http://security.debian.org]("http://security.debian.org/") squeeze/updates Release.gpg
   Could not resolve 'security.debian.org'"

and 3 more errors of the same type for 'security.debian.org', and 'ftp.egr.msu.edu' twice.

---

### Post by PhoHammer on 2009-04-23
I tried the ftp.us.debian.org mirror just now and it gives me the same
"could not resolve" error.

---

### Post by PhoHammer on 2009-04-23
Any ideas why two different mirrors can't resolve but I can still
ping google?

---

### Post by JK3mp on 2009-04-23
can you ping anything other than google? well if others are having issue's its probably a server issue. I know ubuntu servers are overloaded...lol doubt that effects debian servers though. Have you tried installing any other Desktop environment, kde? or perhaps openbox etc. Or really just anything from the repositories?

---

### Post by PhoHammer on 2009-04-23
> **JK3mp said:**
> can you ping anything other than google? well if others are having issue's its probably a server issue. I know ubuntu servers are overloaded...lol doubt that effects debian servers though. Have you tried installing any other Desktop environment, kde? or perhaps openbox etc. Or really just anything from the repositories?

I pinged ubuntuforums.org and it worked. I tried apt-get install kde-desktop-environment
and apt-get install audacity and both give me that same error. I don't see
why debian servers would be down today, especially two of them.

Does anyone want to try downloading a package from the ftp.us.debian.org repo?

---

### Post by PhoHammer on 2009-04-23
So I setup a usb drive to install from via unetbootin and selected testing amd64 netinst and 
I am in the middle of downloading software packages for standard system, laptop, and desktop environment!

It must have been something to do with that iso disc...hmm..

Now let's hope that unetbootin's iso it downloaded is nice and up to date!

Thanks for your help everyone.

---

