---
title: "Bind9 not working reverse zone"
date: 2017-02-23
forum: Debian
---

### Post by carinavb on 2017-02-23
[COLOR=#000000][FONT=&quot]Hello everybody, I recently change my OS to debian jessie and I can't make the server work properly.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]/etc/resolv.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]================[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]nameserver xxx.yyy.zzz.2[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]nameserver 8.8.8.8[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]nameserver 8.8.4.4[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]hosts[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]======[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]/hosts[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]127.0.0.1 localhost[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]xxx.yyy.zzz.2 ns1.midominio.com ns1[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]named.conf.local[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]================[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]include "/etc/bind/named.conf.log";[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]//JUJUYTEL[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]//directa[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]zone "midominio.com" IN {[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]type master;[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]file "/etc/bind/directa/midominio.com1";[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]allow-query { any; };[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]};[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]//reversa[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]zone "zzz.yyy.xxx.IN-ADDR.ARPA" {[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]type master;[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]file "/etc/bind/midominio.com.reversa";[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]allow-query { any; };[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]};[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]//WEBMAIL[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]//directa[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]zone "webmail.midominio.com" IN {[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]type master;[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]file "/etc/bind/webmail.midominio.com";[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]allow-query { any; };[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]};[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]//MAIL[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]//directa[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]zone "mail.midominio.com" IN {[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]type master;[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]file "/etc/bind/mail.midominio.com";[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]allow-query { any; };[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]};[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]named.conf.options[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]==================[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]options {[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]directory "/var/cache/bind";[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]forwarders {[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]8.8.8.8;[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]};[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]version "No version";[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]auth-nxdomain no; # conform to RFC1035[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]allow-query { any; };[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]rate-limit {[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]responses-per-second 10;[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]};[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]};[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]zone midominio.com[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]====================[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]$ORIGIN midominio.com.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]$TTL 1W[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]@ IN SOA ns1.midominio.com. root.ns1.midominio.com. ([/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]2017022005 ; Serial[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]3600 ; Refresh[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]300 ; Retry[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]1209600 ; Expire[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]3600 ; Minimum[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot])[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]IN NS ns1.midominio.com.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]IN NS web.midominio.com.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]IN NS ns1.arnet.com.ar.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]IN NS ns2.arnet.com.ar.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]IN MX 0 mail.midominio.com.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot];--------------------------------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]localhost IN A 127.0.0.1[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]ns1 IN A xxx.yyy.zzz.2[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]IN HINFO DNS Server[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]web IN A xxx.yyy.zzz.5[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]IN HINFO Web Server[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]mail IN A xxx.yyy.zzz.6[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]IN HINFO Mail Server[/FONT][/COLOR]


[COLOR=#000000][FONT=&quot]www IN CNAME web.midominio.com.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]webmail IN CNAME mail.midominio.com.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]proxy IN CNAME ns1.midominio.com.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]reverse zone[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]============[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot];[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]; BIND reverse data file for local loopback interface[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot];[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]$TTL 604800[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]@ IN SOA ns1.midominio.com. root.midominio.com. ([/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]2017022002 ; Serial[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]604800 ; Refresh[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]86400 ; Retry[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]2419200 ; Expire[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]604800 ) ; Negative Cache TTL[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot];[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]@ IN NS ns1.midominio.com.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]2 IN PTR ns1.midominio.com.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]5 IN PTR web.midominio.com.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]6 IN PTR mail.midominio.com.[/FONT][/COLOR]


[COLOR=#000000][FONT=&quot]I get this error[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]============[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]nslookup[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]> xxx.yyy.zzz.2[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot];; Got SERVFAIL reply from xxx.yyy.zzz.2, trying next server[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot];; Got SERVFAIL reply from 8.8.8.8, trying next server[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Server: 8.8.4.4[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Address: 8.8.4.4#53[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]** server can't find 2.zzz.yyy.xxx.in-addr.arpa: SERVFAIL[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]I hope someone can guide me with this.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Best regards.[/FONT][/COLOR]

---

### Post by howefield on 2017-02-23
Moved to the "*Debian*" forum.

---

### Post by SeijiSensei on 2017-02-23
> **carinavb said:**
> ```

//reversa
zone "zzz.yyy.xxx.IN-ADDR.ARPA"
type master;[/FONT][/COLOR]
file "/etc/bind/midominio.com.reversa";
allow-query { any; };
};

//reverse zone
$TTL 604800
@ IN SOA ns1.midominio.com. root.midominio.com. (
2017022002 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS ns1.midominio.com.
2 IN PTR ns1.midominio.com.
5 IN PTR web.midominio.com.
6 IN PTR mail.midominio.com.


```


If the "reverse zone" listing is the contents of /etc/bind/midominio.com.reversa, then to begin with it has the wrong domain in the SOA.  It should read
```
@   IN   SOA  zzz.yyy.xxx.IN-ADDR.ARPA root.midominio.com.
```

---

### Post by carinavb on 2017-02-23
Thanks for the answer....
I did what you said but I still get servfail

$TTL    604800
@       IN      SOA     zzz.yyy.xxx.in-addr.arpa. admin.midominio.com. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;


; Name servers
        IN      NS      ns1.midominio.com.
        IN      NS      web.midominio.com.


; PTR records
2       IN      PTR      ns1.midominio.com.
5       IN      PTR      web.midominio.com.
5       IN      PTR      [www.midominio.com](www.midominio.com).
126     IN      PTR      auth.midominio.com






root@ns1:/etc/bind# nslookup
> xxx.yyy.zzz.6
;; Got SERVFAIL reply from xxx.yyy.zzz.2, trying next server
;; Got SERVFAIL reply from 8.8.8.8, trying next server
Server:         8.8.4.4
Address:        8.8.4.4#53


** server can't find 6.zzz.yyy.xxx.in-addr.arpa: SERVFAIL
> xxx.yyy.zzz.2
;; Got SERVFAIL reply from xxx.yyy.zzz.2, trying next server
;; Got SERVFAIL reply from 8.8.8.8, trying next server
Server:         8.8.4.4
Address:        8.8.4.4#53


** server can't find 2.zzz.yyy.xxx.in-addr.arpa: SERVFAIL
> ns1.midominio.com
Server:         xxx.yyy.zzz.2
Address:        xxx.yyy.zzz.2#53


Name:   ns1.midominio.com
Address: xxx.yyy.zzz.2
> xxx.yyy.zzz.5
;; Got SERVFAIL reply from xxx.yyy.zzz.2, trying next server
;; Got SERVFAIL reply from 8.8.8.8, trying next server
Server:         8.8.4.4
Address:        8.8.4.4#53


** server can't find 5.zzz.yyy.xxx.in-addr.arpa: SERVFAIL
Best Regards..

---

### Post by SeijiSensei on 2017-02-23
Did you restart named either from the prompt or by rebooting?  In my named.conf I have
```

zone "1.1.10.IN-ADDR.ARPA" {
        type master;
        file "10.1.1.rev";
};

```
and the file 10.1.1.rev looks like this:
```

$TTL    86400
@       IN      SOA     1.1.10.in-addr.arpa. root.localhost.  (
                        2014012702 ; Serial
                        28800      ; Refresh
                        14400      ; Retry
                        3600000    ; Expire
                        86400 )    ; Minimum
                                      
        IN      NS      ns.example.com.

1       IN      PTR     smtp.example.com.
12      IN      PTR     mail.example.com.

```
The command "host 10.1.1.12" returns
```

$ host 10.1.1.12
12.1.1.10.in-addr.arpa domain name pointer mail.example.com.

```
That seems to be a parallel configuration to yours, so I don't know why it doesn't work unless you didn't restart the nameserver.

Do you see an entry like this in /var/log/syslog if you restart the nameserver:
```

Feb 23 20:07:14 ns named[15089]: zone 1.1.10.IN-ADDR.ARPA/IN: sending notifies (serial 2014012702)

```

---

### Post by papibe on 2017-02-23
Hi carinavb.

Are you using AppArmor? If so, take a look at [this]("https://ubuntuforums.org/showthread.php?t=2331526&p=13521225#post13521225"). You may need to move your config files to other directory.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by carinavb on 2017-02-24
Thanks a lot for the reply's, I found the error.
I have comments in my named.conf.local, I delete those lines and worked again.
Thanks a lot.
I have another issue, in my named.conf.option change recursion to NO, but now I get Status REFUSED.
I have another question.
I have a different domain that I need to delegate, how I can do that?
Best Regards...

---

### Post by SeijiSensei on 2017-02-24
About recursion: [https://kb.isc.org/article/AA-00269/0/What-has-changed-in-the-behavior-of-allow-recursion-and-allow-query-cache.html](https://kb.isc.org/article/AA-00269/0/What-has-changed-in-the-behavior-of-allow-recursion-and-allow-query-cache.html)

I have recursion enabled in my public DNS servers.

I don't know what you mean about "delegating" a domain? Are you talking about setting up the appropriate files in BIND? Just add another domain to named.conf and a corresponding zone file.  Make sure your server is the designated primary for the domain at your registrar.

---

### Post by carinavb on 2017-03-01
I realize that I have another trouble in the server....
When I use the command nslookup....

root@ns1:/etc/bind# nslookup midominio.com
Server:         xxx.yyy.zzz.2
Address:        xxx.yyy.zzz.2#53


*** Can't find midominio.com: No answer


root@ns1:/etc/bind# nslookup [www.midominio.com]("http://www.midominio.com")
Server:         xxx.yyy.zzz.2
Address:        xxx.yyy.zzz.2#53


[www.midominio.com]("http://www.midominio.com")     canonical name = midominio.com.


The answer is ok with [www.midominio.com](www.midominio.com), when I use midominio.com I have no answer.

Why? What I'm doing wrong?
Regards

---

### Post by carinavb on 2017-03-01
I realize that I have another trouble in the server....
When I use the command nslookup....

root@ns1:/etc/bind# nslookup midominio.com
Server:         xxx.yyy.zzz.2
Address:        xxx.yyy.zzz.2#53


*** Can't find midominio.com: No answer


root@ns1:/etc/bind# nslookup [www.midominio.com](www.midominio.com)
Server:         xxx.yyy.zzz.2
Address:        xxx.yyy.zzz.2#53


[www.midominio.com](www.midominio.com)     canonical name = midominio.com.


Why? What I'm doing wrong?

"[COLOR=#000000]I don't know what you mean about "delegating" a domain? Are you talking about setting up the appropriate files in BIND? Just add another domain to named.conf and a corresponding zone file. Make sure your server is the designated primary for the domain at your registrar.[/COLOR]"
I have another domain otrodominio.com, I have to create a different zone pointed to the same server that point midominio.com? 
Both are in the same server.
Regards

---

