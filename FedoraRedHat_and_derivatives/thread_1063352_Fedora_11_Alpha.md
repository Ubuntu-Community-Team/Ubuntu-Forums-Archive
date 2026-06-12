---
title: "Fedora 11 Alpha"
date: 2009-02-07
forum: Fedora/RedHat and derivatives
---

### Post by Rokurosv on 2009-02-07
So anyone trying it? I'm on it right now and for me the boot is a little faster than 10. The only thing that did bother me is that the LiveCD has problems with ext4 so you can't install it by default only with the DVD, but you can still make them ext 4 later.

---

### Post by Noblacktie on 2009-02-07
That's a bug in the current LiveCD, and note that you can't boot from an EXT4 partition (read release notes). 

You need /boot to be in EXT3. Everything else can be EXT4.

---

### Post by Eclipse. on 2009-02-07
> **Noblacktie said:**
> That's a bug in the current LiveCD, and note that you can't boot from an EXT4 partition (read release notes). 

You need /boot to be in EXT3. Everything else can be EXT4.

Lol I thought they would patch grub like we have with Jaunty so you can boot ext4.

---

### Post by Rokurosv on 2009-02-07
Yeah you can't boot from ext4 yet, all I did was create a 200 MB /boot partition in ext 3, and the other ones I'm in the process of converting them to ext4

---

### Post by Antman on 2009-02-07
I have the alpha installed on my spare laptop. It runs well so far. I can't wait to see the new theme, since the alpha is still using the f10 theme.

---

### Post by Noblacktie on 2009-02-08
> **Eclipse. said:**
> Lol I thought they would patch grub like we have with Jaunty so you can boot ext4.

Funnily enough, the devs feel that GRUB2 is still too unreliable when it comes to making sure the computer boots up without issue.

Who woulda thunk it, Ubuntu more 'bleeding edge' than Fedora? :D

---

### Post by Vince4Amy on 2009-02-08
I've only just got my installation 10 set up and configured the way I like it, so I won't install 11 on hardware until 3-4 months after the final is released. However I Will give this a try on Virtualbox, does it have KDE 4.2?

---

### Post by YeOK on 2009-02-08
> **Vince4Amy said:**
> I've only just got my installation 10 set up and configured the way I like it, so I won't install 11 on hardware until 3-4 months after the final is released. However I Will give this a try on Virtualbox, does it have KDE 4.2?

You can get KDE 4.2 on Fedora 10. Its in the testing repo.

Just enabled testing, and update kde.

```

yum --enablerepo=u*g update kde*

```

---

### Post by Antman on 2009-02-08
> **Vince4Amy said:**
> However I Will give this a try on Virtualbox, does it have KDE 4.2?

Yes, the F11 alpha has KDE4.2

---

