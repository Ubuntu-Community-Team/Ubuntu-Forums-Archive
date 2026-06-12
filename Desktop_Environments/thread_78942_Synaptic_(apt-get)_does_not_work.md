---
title: "Synaptic (apt-get) does not work"
date: 2005-10-19
forum: Desktop Environments
---

### Post by giamax on 2005-10-19
0. Box: Pentium 4; 1 GiB RAM; Intel pro 100 LAN; GeForce 5600; 120 GiB HDD.
1. Configuring DHCP to reserve IP and settings for ubuntu-box (ip = 172.16.100.100, dns = 172.16.1.1, router = 172.16.1.2 - isa 2004 server).
2. Creating on isa server new rule to pass all traffic from 172.16.100.100 to Internet. Allowind Integrated, digest and simple authorization methods.
3. Installing Ubuntu Breezy Badger 5.10 from CD-RW (downloaded from net on 18th of October) to an empty HDD with auto partitioning. The main language is Russian, location - Moscow.
4. Logging in.
5. Launching Synaptic.
6. Adding custom repository "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe main restricted".
7. Synaptic asks "You need to reload the package list from the servers for your changes to take effect. Do you want to do this now?" Answering Yes.
8. Getting error message about impossibility of getting repository info and "http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 403 Forbidden ( The ISA Server denied the specified Uniform Resource Locator (URL).  ) [IP: 82.211.81.151 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) 403 Forbidden ( The ISA Server denied the specified Uniform Resource Locator (URL).  ) [IP: 82.211.81.167 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) 403 Forbidden ( The ISA Server denied the specified Uniform Resource Locator (URL).  ) [IP: 82.211.81.167 80]
[http://ru.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://ru.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 403 Forbidden ( The ISA Server denied the specified Uniform Resource Locator (URL).  ) [IP: 82.211.81.167 80]
[http://ru.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://ru.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) 403 Forbidden ( The ISA Server denied the specified Uniform Resource Locator (URL).  ) [IP: 82.211.81.182 80]
[http://ru.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://ru.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) 403 Forbidden ( The ISA Server denied the specified Uniform Resource Locator (URL).  ) [IP: 82.211.81.193 80]"
9. Getting error "W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1072;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1099; &#1089;&#1087;&#1080;&#1089;&#1082;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1089; &#1080;&#1089;&#1093;&#1086;&#1076;&#1085;&#1099;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080; [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1072;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1099; &#1089;&#1087;&#1080;&#1089;&#1082;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1089; &#1080;&#1089;&#1093;&#1086;&#1076;&#1085;&#1099;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080; [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1072;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1099; &#1089;&#1087;&#1080;&#1089;&#1082;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1089; &#1080;&#1089;&#1093;&#1086;&#1076;&#1085;&#1099;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080; [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1072;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1099; &#1089;&#1087;&#1080;&#1089;&#1082;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1089; &#1080;&#1089;&#1093;&#1086;&#1076;&#1085;&#1099;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080; [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1072;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1099; &#1089;&#1087;&#1080;&#1089;&#1082;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1089; &#1080;&#1089;&#1093;&#1086;&#1076;&#1085;&#1099;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080; [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1072;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1099; &#1089;&#1087;&#1080;&#1089;&#1082;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1089; &#1080;&#1089;&#1093;&#1086;&#1076;&#1085;&#1099;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080; [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)"

What should I do?

---

### Post by aysiu on 2005-10-19
I've read in several places that people should take the us out of us.archive.ubuntu.com. Maybe you should take the ru out of ru.archive.ubuntu.com

For a working sources.list, go here:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by argosreality on 2005-10-19
It looks also like you're behind an Microsoft ISA firewall that might be blocking apt-get upgrades. Or it could just be blocking the specific sources you're trying to grab from.

---

### Post by giamax on 2005-10-20
Yes, there IS a problem with getting packages through HTTP protocol. But there is NO problem with FTP :) . Yes, pretty simple :D  Just change http:// to ftp:// when adding repositories and things will work!

Best regards,
Giamax.

---

