---
title: "Pidgin problems even witn msn-pecan"
date: 2009-06-02
forum: General Help
---

### Post by ili on 2009-06-02
One month ago my msn account stop functioning and still now i don't know why is happening that.
I have the last version and i´ve tried the msn-pecan plugin without any luck.
I had a doubt if it could be because of the proxy or firewall at my work so i installed msn live or whatever it´s name be and it works fine.
I also have tried the advanced features like http method and nothing.
The next solution was unistall everything and ...nothing.
Anyone has suffered this, if so any solution?

There is the debug:

```

12:35:57) account: Connecting to account 
(12:35:57) connection: Connecting. gc = 0442E770
(12:35:57) msn: new httpconn (043AF5F8)
(12:35:57) proxy: No Windows proxy set.
(12:35:57) dnsquery: Performing DNS lookup for messenger.hotmail.com
(12:35:57) dnsquery: IP resolved for messenger.hotmail.com
(12:35:57) proxy: Attempting connection to 65.54.52.62
(12:35:57) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(12:35:57) proxy: Connection in progress
(12:35:57) proxy: Connecting to messenger.hotmail.com:1863.
(12:35:57) msn: C: NS 000: VER 1 MSNP15 CVR0
(12:35:58) msn: S: NS 000: VER 1 MSNP15
(12:35:58) msn: C: NS 000: CVR 2 0x0409 winnt 5.1 i386 MSNMSGR 8.5.1302 BC01 
(12:35:58) msn: S: NS 000: CVR 2 14.0.8064 14.0.8064 8.1.0178 http://msgr.dlservice.microsoft.com/download/5/2/E/52EB299A-E4DE-43E2-8D55-510D7FB03610/en/wlsetup-cvr.exe http://download.live.com/?sku=messenger
(12:35:58) msn: C: NS 000: USR 3 SSO I 
(12:35:58) msn: S: NS 000: XFR 3 NS 65.54.49.55:1863 U D
(12:35:58) proxy: No Windows proxy set.
(12:35:58) dnsquery: Performing DNS lookup for 65.54.49.55
(12:35:58) dnsquery: IP resolved for 65.54.49.55
(12:35:58) proxy: Attempting connection to 65.54.49.55
(12:35:58) proxy: Connecting to 65.54.49.55:1863 with no proxy
(12:35:58) proxy: Connection in progress
(12:35:58) proxy: Connecting to 65.54.49.55:1863.
(12:35:58) msn: C: NS 000: VER 4 MSNP15 CVR0
(12:35:58) msn: S: NS 000: VER 4 MSNP15
(12:35:58) msn: C: NS 000: CVR 5 0x0409 winnt 5.1 i386 MSNMSGR 8.5.1302 BC01 ilikahua@hotmail.com
(12:35:59) util: Writing file prefs.xml to directory C:\Users
(12:35:59) util: Writing file C:\Users....\prefs.xml
(12:36:01) msn: S: NS 000: CVR 5 14.0.8064 14.0.8064 8.1.0178 http://msgr.dlservice.microsoft.com/download/5/2/E/52EB299A-E4DE-43E2-8D55-510D7FB03610/en/wlsetup-cvr.exe http://download.live.com/?sku=messenger
(12:36:01) msn: C: NS 000: USR 6 SSO I 
(12:36:01) jabber: Sending (ssl): <iq type='get' id='purplea31f0b15'><ping xmlns='urn:xmpp:ping'/></iq>
(12:36:01) jabber: Recv (ssl)(71): <iq type="result"/>
(12:36:01) msn: S: NS 000: GCF 0 6735
(12:36:01) msn: Processing GCF command
(12:36:02) util: Writing file accounts.xml to directory C:\Users\....\.purple
(12:36:02) util: Writing file C:\Users....accounts.xml
(12:36:03) msn: S: NS 000: USR 6 SSO S MBI_KEY_OLD 70IiYat3/K7Edq36phKFF169lwY2qwEIJRp5d0asWZlKlA3rIlZQxqlivhIKeuXH
(12:36:03) msn: Starting Windows Live ID authentication
(12:36:03) msn: Logging on ..., with policy 'MBI_KEY_OLD', nonce '70IiYat3/K7Edq36phKFF169lwY2qwEIJRp5d0asWZlKlA3rIlZQxqlivhIKeuXH'
(12:36:03) proxy: No Windows proxy set.
(12:36:03) dnsquery: Performing DNS lookup for login.live.com
(12:36:03) dnsquery: IP resolved for login.live.com
(12:36:03) proxy: Attempting connection to 65.54.186.17
(12:36:03) proxy: Connecting to login.live.com:443 with no proxy
(12:36:03) proxy: Connection in progress


```

---

### Post by whoop on 2009-06-02
Same problems with amsn or empathy? Just to  make sure it's not client/application related...

---

### Post by ili on 2009-06-03
Today i tried with amsn and yep, there is again the same problem.
It keeps trying to connect but nothing.
I'm trying it from wind0ws v1st4 but there should be no problem.

What else could be?:(

---

### Post by ili on 2009-06-08
help!!!
I'm still looking for a solution.

---

### Post by khc on 2009-06-09
paste the full debug log after you removed msn-pecan and I can take a look

---

### Post by ili on 2009-06-10
There is the log:
```

10:00:47) account: Connecting to account
(10:00:47) connection: Connecting. gc = 04424558
(10:00:47) msn: new httpconn (04423408)
(10:00:47) proxy: No Windows proxy set.
(10:00:47) dnsquery: Performing DNS lookup for messenger.hotmail.com
(10:00:47) dnsquery: IP resolved for messenger.hotmail.com
(10:00:47) proxy: Attempting connection to 65.54.239.20
(10:00:47) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(10:00:47) proxy: Connection in progress
(10:00:47) proxy: Connecting to messenger.hotmail.com:1863.
(10:00:47) msn: C: NS 000: VER 1 MSNP15 CVR0
(10:00:48) msn: S: NS 000: VER 1 MSNP15
(10:00:48) msn: C: NS 000: CVR 2 0x0409 winnt 5.1 i386 MSNMSGR 8.5.1302 BC01 
(10:00:48) msn: S: NS 000: CVR 2 14.0.8064 14.0.8064 8.1.0178 http://msgr.dlservice.microsoft.com/download/5/2/E/52EB299A-E4DE-43E2-8D55-510D7FB03610/en/wlsetup-cvr.exe http://download.live.com/?sku=messenger
(10:00:48) msn: C: NS 000: USR 3 SSO I 
(10:00:48) msn: S: NS 000: XFR 3 NS 207.46.124.147:1863 U D
(10:00:48) proxy: No Windows proxy set.
(10:00:48) dnsquery: Performing DNS lookup for 207.46.124.147
(10:00:48) dnsquery: IP resolved for 207.46.124.147
(10:00:48) proxy: Attempting connection to 207.46.124.147
(10:00:48) proxy: Connecting to 207.46.124.147:1863 with no proxy
(10:00:48) proxy: Connection in progress
(10:00:51) proxy: Connecting to 207.46.124.147:1863.
(10:00:51) msn: C: NS 000: VER 4 MSNP15 CVR0
(10:00:51) msn: S: NS 000: VER 4 MSNP15
(10:00:51) msn: C: NS 000: CVR 5 0x0409 winnt 5.1 i386 MSNMSGR 8.5.1302 BC01 
(10:00:51) msn: S: NS 000: CVR 5 14.0.8064 14.0.8064 8.1.0178 http://msgr.dlservice.microsoft.com/download/5/2/E/52EB299A-E4DE-43E2-8D55-510D7FB03610/en/wlsetup-cvr.exe http://download.live.com/?sku=messenger
(10:00:51) msn: C: NS 000: USR 6 SSO I 
(10:00:52) msn: S: NS 000: GCF 0 6735
(10:00:52) msn: Processing GCF command
(10:00:52) util: Writing file accounts.xml to directory C:\Users\.purple
(10:00:52) util: Writing file C:\Users\\.purple\accounts.xml
(10:00:54) autorecon: do_signon called
(10:00:54) autorecon: calling purple_account_connect
(10:00:54) account: Connecting to account 
(10:00:54) autorecon: done calling purple_account_connect
(10:00:56) msn: S: NS 000: USR 6 SSO S MBI_KEY_OLD 5UOfGRTiIqcsbKj5HEHPpqynMxXKrz2/fny6fyiXLoukhWSEvr81ikGcBqjzqJVG
(10:00:56) msn: Starting Windows Live ID authentication
(10:00:56) msn: Logging on , with policy 'MBI_KEY_OLD', nonce '5UOfGRTiIqcsbKj5HEHPpqynMxXKrz2/fny6fyiXLoukhWSEvr81ikGcBqjzqJVG'
(10:00:56) proxy: No Windows proxy set.
(10:00:56) dnsquery: Performing DNS lookup for login.live.com
(10:00:56) dnsquery: IP resolved for login.live.com
(10:00:56) proxy: Attempting connection to 65.54.186.77
(10:00:56) proxy: Connecting to login.live.com:443 with no proxy
(10:00:56) proxy: Connection in progress
(10:01:17) proxy: Connecting to login.live.com:443.
(10:01:17) proxy: Error connecting to login.live.com:443 (Expiró la conexión.).
(10:01:17) proxy: Connection attempt failed: Expiró la conexión.
(10:01:17) msn: C: NS 000: OUT
(10:01:17) account: Disconnecting account 022D05B8
(10:01:17) connection: Disconnecting connection 04424558
(10:01:17) msn: destroy the OIM 0444A598
(10:01:17) msn: destroy httpconn (04423408)
(10:01:17) jabber: jabber_actions: have pep: NO
(10:01:17) connection: Destroying connection 04424558
(10:01:22) util: Writing file accounts.xml to directory C:\Users\\.purple
(10:01:22) util: Writing file C:\Users\\.purple\accounts.xml

```

Would be helpful?

---

### Post by khc on 2009-06-11
looks like you can't connect to login.live.com:443, which would indicates that it's either a firewall or proxy problem. It's possible that the official client reads some proxy settings that pidgin doesn't know about or work around by using another way to connect.

what are you doing asking a windows environment problem in an Ubuntu forum anyway :-P

---

### Post by ili on 2009-06-11
> **khc said:**
> 
what are you doing asking a windows environment problem in an Ubuntu forum anyway :-P

Like i have installed ubuntu at home and at work i use windows but the same im(pidgin) on both computers.
Besides that on the pidgin site there is no response about this issue and thanks to your response now I know what am I looking...;)=D>

---

