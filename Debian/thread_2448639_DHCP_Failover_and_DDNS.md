---
title: "DHCP Failover and DDNS"
date: 2020-08-11
forum: Debian
---

### Post by bombadas on 2020-08-11
Hello everyone!
I'm a newbie here and with Linux. 
I explain my situation, I have a school projet in Linux to do. 
I'm trying to do a dhcp failover with DDNS. I have a Debian and Centos. When I restart the services, in both servers, everything seems ok, but when I start a client I have an "unexpected error". I search everywhere but I can not understand (find) the problem. 
If someone can help me I'll appreciate it.
Thank you for the help!

Debian dhcp.conf
[FONT=Monaco]authoritative;[/FONT]
[FONT=Monaco]log-facility local7;[/FONT]
[FONT=Monaco]failover peer "failover" {[/FONT]
[FONT=Monaco]     primary;[/FONT]
[FONT=Monaco]     address 192.168.2.250;[/FONT]
[FONT=Monaco]     port 519;[/FONT]
[FONT=Monaco]     peer address 192.168.2.251; [/FONT]
[FONT=Monaco]     peer port 520;[/FONT]
[FONT=Monaco]     max-response-delay 60;[/FONT]
[FONT=Monaco]     max-unacked-updates 10;[/FONT]
[FONT=Monaco]     mclt 3600;[/FONT]
[FONT=Monaco]     split 128;[/FONT]
[FONT=Monaco]     load balance max seconds 3;[/FONT]
[FONT=Monaco]}[/FONT]
[FONT=Monaco]ddns-updates on;[/FONT]
[FONT=Monaco]ddns-update-style standard;[/FONT]
[FONT=Monaco]ddns-domainname "tux.labo";[/FONT]
[FONT=Monaco]ddns-rev-domainname "2.168.192.in-addr.arpa";[/FONT]
[FONT=Monaco]include "/etc/dhcp/tux.key";[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]zone tux.labo {[/FONT]
[FONT=Monaco]    primary 192.168.2.250;[/FONT]
[FONT=Monaco]    key tux-key;[/FONT]
[FONT=Monaco]    }[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]zone 2.168.192.in-addr.arpa. {[/FONT]
[FONT=Monaco]    primary 192.168.2.250;[/FONT]
[FONT=Monaco]    key tux-key;[/FONT]
[FONT=Monaco]    }[/FONT]
[FONT=Monaco]
[/FONT]
[FONT=Monaco]subnet 192.168.2.0 netmask 255.255.255.0 {[/FONT]
[FONT=Monaco]  option domain-name-servers 192.168.2.250, 192.168.2.251;[/FONT]
[FONT=Monaco]  option domain-name "tux.labo";[/FONT]
[FONT=Monaco]  option routers 192.168.2.254;[/FONT]
[FONT=Monaco]  default-lease-time 600;[/FONT]
[FONT=Monaco]  max-lease-time 7200;[/FONT]
[FONT=Monaco]  pool {[/FONT]
[FONT=Monaco]    failover peer "failover";[/FONT]
[FONT=Monaco]      range 192.168.2.1    192.168.2.100;[/FONT]
[FONT=Monaco]    }[/FONT]
[FONT=Monaco]}[/FONT]


Restart bind9
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: automatic empty zone: B.E.F.IP6.ARPA[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: automatic empty zone: EMPTY.AS112.ARPA[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: automatic empty zone: HOME.ARPA[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: none:106: 'max-cache-size 90%' - setting to 888MB (out of 98[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: configuring command channel from '/etc/bind/rndc.key'[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: command channel listening on 127.0.0.1#953[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: configuring command channel from '/etc/bind/rndc.key'[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: command channel listening on ::1#953[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: managed-keys-zone: loaded serial 7[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: reverse.dns:12: ignoring out-of-zone data (250)[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: reverse.dns:13: ignoring out-of-zone data (251)[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: zone 2.168.192.in-addr.arpa/IN: loaded serial 29[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: zone tux.labo/IN: loaded serial 53[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: all zones loaded[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb systemd[1]: Started BIND Domain Name Server.[/FONT]
[FONT=Monaco]-- Subject: L'unité (unit) bind9.service a terminé son démarrage[/FONT]
[FONT=Monaco]-- Defined-By: systemd[/FONT]
[FONT=Monaco]-- Support: [/FONT][COLOR=#F4F4F4][FONT=Monaco][https://www.debian.org/support](https://www.debian.org/support)[/FONT][/COLOR]
[FONT=Monaco]-- [/FONT]
[FONT=Monaco]-- L'unité (unit) bind9.service a terminé son démarrage, avec le résultat done.[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: running[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: zone 2.168.192.in-addr.arpa/IN: sending notifies (serial 29)[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: zone tux.labo/IN: sending notifies (serial 53)[/FONT]

Centos - dhcp.conf
[FONT=Courier]authoritative;[/FONT]
[FONT=Courier]
[/FONT]
[FONT=Courier]failover peer "failover" {[/FONT]
[FONT=Courier]     secondary;[/FONT]
[FONT=Courier]     address 192.168.2.251;[/FONT]
[FONT=Courier]     port 520;[/FONT]
[FONT=Courier]     peer address 192.168.2.250;[/FONT]
[FONT=Courier]     peer port 519;[/FONT]
[FONT=Courier]     max-response-delay 60;[/FONT]
[FONT=Courier]     max-unacked-updates 10;[/FONT]
[FONT=Courier]     load balance max seconds 3;[/FONT]
[FONT=Courier]}[/FONT]
[FONT=Courier]
[/FONT]
[FONT=Courier]ddns-updates on;[/FONT]
[FONT=Courier]ddns-update-style standard;[/FONT]
[FONT=Courier]ddns-domainname "tux.labo";[/FONT]
[FONT=Courier]ddns-rev-domainname "2.168.192.in-addr.arpa";[/FONT]
[FONT=Courier]
[/FONT]
[FONT=Courier]zone tux.labo {[/FONT]
[FONT=Courier]    primary 192.168.2.250;[/FONT]
[FONT=Courier]    }[/FONT]
[FONT=Courier]
[/FONT]
[FONT=Courier]zone 2.168.192.in-addr.arpa {[/FONT]
[FONT=Courier]    primary 192.168.2.250;[/FONT]
[FONT=Courier]    }[/FONT]
[FONT=Courier]
[/FONT]
[FONT=Courier]subnet 192.168.2.0 netmask 255.255.255.0 {[/FONT]
[FONT=Courier]    option domain-name-servers 192.168.2.251, 192.168.2.250;[/FONT]
[FONT=Courier]    option domain-name "tux.labo";[/FONT]
[FONT=Courier]    option routers 192.168.2.254;[/FONT]
[FONT=Courier]    default-lease-time 600;[/FONT]
[FONT=Courier]    max-lease-time 7200;[/FONT]
[FONT=Courier]    pool {[/FONT]
[FONT=Courier]        failover peer "failover";[/FONT]
[FONT=Courier]        range 192.168.2.1    192.168.2.100;[/FONT]
[FONT=Courier]        }[/FONT]
[FONT=Courier]}[/FONT]

journalctl -f Debian

[FONT=Monaco]oût 11 10:47:44 srv-deb named[768]: zone 2.168.192.in-addr.arpa/IN: loaded serial 29[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: zone tux.labo/IN: loaded serial 53[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: all zones loaded[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb systemd[1]: Started BIND Domain Name Server.[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: running[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: zone 2.168.192.in-addr.arpa/IN: sending notifies (serial 29)[/FONT]
[FONT=Monaco]août 11 10:47:44 srv-deb named[768]: zone tux.labo/IN: sending notifies (serial 53)[/FONT]
[FONT=Monaco]août 11 10:49:39 srv-deb dhcpd[722]: DHCPREQUEST for 192.168.2.2 from 08:00:27:43:a3:01 (edgar-PC) via enp0s3[/FONT]
[FONT=Monaco]août 11 10:49:39 srv-deb dhcpd[722]: DHCPACK on 192.168.2.2 to 08:00:27:43:a3:01 (edgar-PC) via enp0s3[/FONT]
[FONT=Monaco]août 11 10:49:49 srv-deb dhcpd[722]: DHCPINFORM from 192.168.2.2 via enp0s3[/FONT]
[FONT=Monaco]août 11 10:49:49 srv-deb dhcpd[722]: DHCPACK to 192.168.2.2 (08:00:27:43:a3:01) via enp0s3[/FONT]
[FONT=Monaco]août 11 10:49:49 srv-deb named[768]: resolver priming query complete[/FONT]
[FONT=Monaco]août 11 10:49:53 srv-deb named[768]: resolver priming query complete[/FONT]


journalctl -f Centos

[FONT=Courier]-- Logs begin at Tue 2020-08-11 10:36:29 CEST. --[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos named[1618]: zone tux.labo/IN: loaded serial 17[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos named[1618]: zone localhost.localdomain/IN: loaded serial 0[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos named[1618]: zone localhost/IN: loaded serial 0[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos named[1618]: zone 2.168.192.in-addr.arpa/IN: loaded serial 14[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos named[1618]: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.ip6.arpa/IN: loaded serial 0[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos named[1618]: **all zones loaded**[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos named[1618]: **running**[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos systemd[1]: Started Berkeley Internet Name Domain (DNS).[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos named[1618]: zone tux.labo/IN: sending notifies (serial 17)[/FONT]
[FONT=Courier]Aug 11 10:49:00 srv-centos named[1618]: zone 2.168.192.in-addr.arpa/IN: sending notifies (serial 14)[/FONT]
[FONT=Courier]Aug 11 10:49:31 srv-centos dhcpd[1496]: _**failover peer failover: unexpected error**_[/FONT]
[FONT=Courier]Aug 11 10:49:39 srv-centos dhcpd[1496]: DHCPREQUEST for 192.168.2.2 from 08:00:27:43:a3:01 (edgar-PC) via enp0s3[/FONT]
[FONT=Courier]Aug 11 10:49:39 srv-centos dhcpd[1496]: DHCPACK on 192.168.2.2 to 08:00:27:43:a3:01 (edgar-PC) via enp0s3[/FONT]

Because of this error, I can not update the zones file.
Thank you!

---

### Post by slickymaster on 2020-08-11
*Thread moved to **Debian**.*

---

