---
title: "Sidebar on Google Earth not working"
date: 2016-07-09
forum: Desktop Environments
---

### Post by williepabon on 2016-07-09
Hi:
My Google Earth app has been working for the past few months (I use it sporadically) without problems. This morning I opened it up and the side bar stopped working. When I initially open the app the sidebar shows but without inormation. If I, using the menu (View ->Sidebar) turn it off and then on, it won't show. Any ideas to solve this are appreciated. My system inofrmation:

```
williepabon@WP-Macmini:~$ lsb_release -cridDistributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty
williepabon@WP-Macmini:~$ uname -a
Linux WP-Macmini 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

My Google Earth version is 7.1.2.2041
Thanks

---

### Post by squirrel3 on 2016-07-09
Hi ya,

I found this documentation regarding Google Earth. There is a troubleshooting section towards the bottom of the page. I sincerely hope that it helps you. It states that Google Earth for Linux is still in beta. However, it says Google Earth has compiz issues. There are a number of things you can check in the troubleshooting section. Best of luck to you. :)

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by williepabon on 2016-07-11
[[COLOR=#000000]squirrel3[/COLOR]]("http://ubuntuforums.org/member.php?u=2024235")

Thanks for answering. I looked on the link that you suggest, but I couldn't find any hints that address my specific problem. As I said, Google Earth was running OK until, I think, the system software was upgraded to the current version. Accepting additional suggestions.
wp

Additional info to  see if it may help to the solution of this problem.

I opened Google Earth executing the command from a terminal to find out if there were any errors or warnings that would help to solve the problem, and this is what I got:

```
williepabon@WP-Macmini:~$ cd /opt/google/earth/freewilliepabon@WP-Macmini:/opt/google/earth/free$ google-earth
[0712/200640:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0712/200642:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for www.google.com failed err=-8181
[0712/200642:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for kh.google.com failed err=-8181
[0712/200647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0712/200647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0712/200647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0712/200647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0712/200647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0712/200647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0712/200647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0712/200647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000647:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000647:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for support.google.com failed err=-8181
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for mw1.google.com failed err=-8181
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000648:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for ssl.google-analytics.com failed err=-8181
[0713/000648:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for ssl.gstatic.com failed err=-8181
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000649:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for apis.google.com failed err=-8181
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000650:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for khmdb.google.com failed err=-8181
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for csi.gstatic.com failed err=-8181
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000651:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for accounts.google.com failed err=-8181
[0713/000651:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for content.googleapis.com failed err=-8181
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000652:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000657:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for mw2.google.com failed err=-8181
[0713/000657:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000657:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000657:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000657:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000657:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000757:ERROR:x509_certificate_nss.cc(730)] CERT_PKIXVerifyCert for maps.google.com failed err=-8181
[0713/000757:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000757:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000757:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000757:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/000757:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001032:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001032:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001032:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001032:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001032:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001035:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001035:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001035:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001035:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0713/001035:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
```

Maybe there is someone  in this forum who understands this and would give  advice. Thanks.

---

