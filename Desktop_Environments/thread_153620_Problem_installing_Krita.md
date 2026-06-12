---
title: "Problem installing Krita"
date: 2006-04-01
forum: Desktop Environments
---

### Post by dOOd on 2006-04-01
Howdy,
Well I tried installing Krita into Breezy and I have a problem. I tried using Synaptic for the install and everyting seemed to go ok. However when I rebooted and tried to start Krita it fails. Upon further investigation it seems I have a broken package that I can't fix. I tried to install it again using apt but ran into the same problem with a broken package. When I run apt-get -f install here is the output:

> Preconfiguring packages ...
(Reading database ... 102975 files and directories currently installed.)
Unpacking kdelibs-data (from .../kdelibs-data_4%3a3.4.3-0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.3-0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/mimelnk/application/vnd.rn-realmedia.desktop', which is also in package realplay
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.3-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas how I can fix this?

Thanks

---

### Post by dOOd on 2006-04-02
Nobody has any ideas what I need do to fix it? I really would like to check out Krita. I am comfortable with Gimp, but always looking to expand my horizons.

~;-)

---

### Post by GeneralZod on 2006-04-02
[QUOTE=dOOd]Nobody has any ideas what I need do to fix it? I really would like to check out Krita. I am comfortable with Gimp, but always looking to expand my horizons.

~;-)[/QUOTE]

Looks like whoever packaged RealPlayer was careless and conflicted with kdelibs - or vice-versa!

Two ways you could go about this; one safe, the other not so safe:

1) Uninstall RealPlayer and try again; and 
2) NOT RECOMMENDED - 

```

cd /var/cache/apt/archives
sudo dpkg --force-overwrite -i  kdelibs-data_4%3a3.4.3-0ubuntu2_all.deb

```

the latter is really not a good idea and could cause untold damage to your system - or everything could go perfectly well - it's hard to say ;)

---

### Post by dOOd on 2006-04-02
[QUOTE=GeneralZod]Looks like whoever packaged RealPlayer was careless and conflicted with kdelibs - or vice-versa!

Two ways you could go about this; one safe, the other not so safe:

1) Uninstall RealPlayer and try again; and 
2) NOT RECOMMENDED - 

```

cd /var/cache/apt/archives
sudo dpkg --force-overwrite -i  kdelibs-data_4%3a3.4.3-0ubuntu2_all.deb

```

the latter is really not a good idea and could cause untold damage to your system - or everything could go perfectly well - it's hard to say ;)[/QUOTE]

Thanks Zod. Yah I already tried uninstalling Realplayer. No joy there. I really need to get this fixed as I can't use Synaptic or Apt until that package get's fixed. So,
I'll backup my system and then try the dreaded option #2. If you hear an earth shattering Kaboom you'll know how it went.

~;-)

---

### Post by dOOd on 2006-04-02
And I'm pleased to report the --force-overwrite method worked just fine. No earth shattering kaboom. Thanks again Zod.

8)

---

### Post by GeneralZod on 2006-04-03
[QUOTE=dOOd]And I'm pleased to report the --force-overwrite method worked just fine. No earth shattering kaboom. Thanks again Zod.

8)[/QUOTE]

That's a relief ;) Glad it worked!

---

