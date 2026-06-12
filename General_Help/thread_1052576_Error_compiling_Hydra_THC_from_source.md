---
title: "Error compiling Hydra THC from source"
date: 2009-01-27
forum: General Help
---

### Post by ispy on 2009-01-27
I tried several times to compile the Hydra source package, I always get this:

```
troy@ispy-laptop:~$ cd ~/Desktop/hydra-5.4-src
troy@ispy-laptop:~/Desktop/hydra-5.4-src$ /.configure
bash: /.configure: No such file or directory
troy@ispy-laptop:~/Desktop/hydra-5.4-src$ ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... NOT found, SSL support disabled
Get it from http://www.openssl.org
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from http://0xbadc0de.be/ - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
troy@ispy-laptop:~/Desktop/hydra-5.4-src$ make
gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
gcc -I. -Wall -O2 -c hydra-vnc.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-pcnfs.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-rexec.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-nntp.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-socks5.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-telnet.c -DLIBPOSTGRES 
hydra-telnet.c: In function ‘service_telnet’:
hydra-telnet.c:177: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
hydra-telnet.c:191: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
hydra-telnet.c:198: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc -I. -Wall -O2 -c hydra-cisco.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-http.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-ftp.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-imap.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-pop3.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-smb.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-icq.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-cisco-enable.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-ldap.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-mysql.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-http-proxy.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-smbnt.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-mssql.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-snmp.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-cvs.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-smtpauth.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-sapr3.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-ssh2.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-teamspeak.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-postgres.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-rsh.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-rlogin.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-oracle-listener.c -DLIBPOSTGRES 
hydra-oracle-listener.c:10:2: warning: #warning "The Oracle Listener module does not work yet"
gcc -I. -Wall -O2 -c hydra-svn.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-pcanywhere.c -DLIBPOSTGRES 
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function ‘md5_crypt’:
hydra-sip.c:24: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: ‘MD5_CTX’ undeclared (first use in this function)
hydra-sip.c:26: error: expected ‘;’ before ‘c’
hydra-sip.c:31: warning: implicit declaration of function ‘MD5_Init’
hydra-sip.c:31: error: ‘c’ undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function ‘MD5_Update’
hydra-sip.c:33: warning: implicit declaration of function ‘MD5_Final’
hydra-sip.c:24: warning: unused variable ‘md5_raw’
hydra-sip.c: In function ‘sip_register’:
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1
troy@ispy-laptop:~/Desktop/hydra-5.4-src$ sudo make
[sudo] password for troy: 
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function ‘md5_crypt’:
hydra-sip.c:24: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: ‘MD5_CTX’ undeclared (first use in this function)
hydra-sip.c:26: error: expected ‘;’ before ‘c’
hydra-sip.c:31: warning: implicit declaration of function ‘MD5_Init’
hydra-sip.c:31: error: ‘c’ undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function ‘MD5_Update’
hydra-sip.c:33: warning: implicit declaration of function ‘MD5_Final’
hydra-sip.c:24: warning: unused variable ‘md5_raw’
hydra-sip.c: In function ‘sip_register’:
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1
troy@ispy-laptop:~/Desktop/hydra-5.4-src$ make install
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function ‘md5_crypt’:
hydra-sip.c:24: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: ‘MD5_CTX’ undeclared (first use in this function)
hydra-sip.c:26: error: expected ‘;’ before ‘c’
hydra-sip.c:31: warning: implicit declaration of function ‘MD5_Init’
hydra-sip.c:31: error: ‘c’ undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function ‘MD5_Update’
hydra-sip.c:33: warning: implicit declaration of function ‘MD5_Final’
hydra-sip.c:24: warning: unused variable ‘md5_raw’
hydra-sip.c: In function ‘sip_register’:
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1
troy@ispy-laptop:~/Desktop/hydra-5.4-src$
```

It also happens that I get similar errors trying to compile anything from source.

any help?

---

### Post by mc4man on 2009-01-27
Somewhat conflicted as to 'hacking' software so would simply suggest you reread your configure a little more closely.

> checking for openssl (libssl/ssl.h) ...
                                    ... _NOT found_, SSL support disabled
Get it from [http://www.openssl.org](http://www.openssl.org)
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
                                      ... _NOT found,_ module ssh2 disabled
Get it from [http://0xbadc0de.be/](http://0xbadc0de.be/) - _use v0.11!_


---

### Post by ispy on 2009-01-27
thanks. I didn't even see that. Appreciate it.

---

