---
title: "Subversion and HTTPS bug in Jaunty 9.04 - workaround"
date: 2009-06-05
forum: General Help
---

### Post by ororo on 2009-06-05
I refer to a previou thread:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=948900]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=948900")

> If you have upgraded to 8.10 you may suddenly find that using svn against a private https repository no longer works. It refuses to talk to the repository, with the following error:

svn: OPTIONS of 'https://xxxxxxxxxx.xxxx.xx/svn/repo': SSL negotiation failed: SSL error: Key usage violation in certificate has been detected. ([https://xxxxxxxxxxx.xxxx.xx](https://xxxxxxxxxxx.xxxx.xx))

This is because in Intrepid, the neon HTTP library, which Subversion uses to talk to HTTP(S) servers, has been built with GNU TLS instead of OpenSSL.

Well, the problem is still present in Jaunty.
I thanks a lot dcrooke and kalosaurusrex for their solutions.

After having rebuilt svn, I wanted also to recompile rapidsvn (a GUI for svn).
Here is what I did in order to recompile rapidsvn:

```

sudo apt-get install -y libexpat1-dev libaprutil1-dev libwxgtk2.8-dev
sudo apt-get install -y automake autoconf libtool
wget http://www.rapidsvn.org/download/release/0.9.8/rapidsvn-0.9.8.tar.gz
tar xvf rapidsvn-0.9.8.tar.gz
cd rapidsvn-0.9.8
./autogen.sh
./configure --prefix=/usr/local
make
sudo make install
cd ..
rm -rf rapidsvn-0.9.8
rm rapidsvn-0.9.8.tar.gz

```

---

### Post by vvoipio on 2009-08-24
This bug has an interesting background. After digging around a bit further, it seems possible to solve the bug without any recompilation. The recipe below has been tested with Apache2 and Subversion in Ubuntu 9.04.


[B]The quick workaround: 
[/B] 
Disable the use of Diffie-Hellman key exchange in the web server configuration. In Apache this requires changing the SSLCipherSuite value for the server (the configuration file is usually in /etc/apache2/sites-available/xxx) as follows:

  ```
SSLCipherSuite HIGH:MEDIUM:-DH
```The important part here is the -DH option. It instructs OpenSSL used by Apache not to offer the Diffie-Hellman key exchange when negotiating the secured connection. (All https servers using OpenSSL should have a similar option.)

After adding the -DH, restart the server, and Subversion should be happy.


**The explanation:**

(Warning: I am not an expert in cryptography. The following section may contain errors. It is mostly based on untested speculation. Corrections welcome.)

The underlying cause for this behaviour seems to be a feature of OpenSSL. When a self-signed certificate (or self-created-CA-signed certificate) is created, OpenSSL makes a certificate which is not acceptable for DH key exchange if RFC2459 is interpreted strictly. GnuTLS is very strict in interpretation, and so the key exchange fails.

It seems that the OpenSSL-created certificates have two problems in the X509v3 extensions. The first one is that the "Key usage" extension is marked as non-critical (which seems to be in violation with the RFC). The second one is that the keyAgreement bit is missing.

The RFC states: "The keyAgreement bit is asserted when the subject public key is used for key agreement.  For example, when a Diffie-Hellman key is to be used for key management, then this bit shall asserted." So, the correct behaviour is to reject the certificate in DH key exchange if the bit is missing. GnuTLS does exactly this, and after passing the obfuscated error message through a few layers, the Subversion user gets the key violation error message.[FONT=monospace]

[/FONT]So, why did it work earlier (until Ubuntu 8.04)? Because OpenSSL is not so strict. Either it takes the "non-critical" seriously and does not care, or it never cares about the keyAgreement bit. It is even possible that it decides DH key exchange to be no good but tries the other method (RSA).

The best solution would be to make a formally correct certificate (or rather create a new certificate with the correct extensions). That, unfortunately, may not be very straightforward in all cases. The workaround explained in the first section of this post is really a workaround; the server *per se* has nothing to do with the problem.

---

