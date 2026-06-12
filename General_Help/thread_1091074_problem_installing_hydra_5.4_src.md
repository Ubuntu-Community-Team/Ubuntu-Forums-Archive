---
title: "problem installing hydra 5.4 src"
date: 2009-03-09
forum: General Help
---

### Post by computerjunkie on 2009-03-09
Hey all,
I'm trying to create my own linux security toolkit for my senior project. I started with a base server install got gnome and other packages. I'm having trouble installing a couple of them though. Most notably, hydra is giving me some...interesting issues. It configures and makes just fine. (says hydra-gtk won't work, but that./hydra is "ready to go). so I type sudo make install and I get:

chris@HOSTNAME:~/thorn stuff/to be installed/hydra-5.4-src$ sudo make install
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)


I figured it was just something silly and would work, so I tried:

chris@HOSTNAME:~/thorn stuff/to be installed/hydra-5.4-src$ ./hydra
bash: ./hydra: Permission denied
chris@HOSTNAME:~/thorn stuff/to be installed/hydra-5.4-src$ sudo ./hydra
sudo: ./hydra: command not found


permission is denied, to a non-existent shell script? um ok. Well, needless to say I'm a little confused. I saw someone on another site had this same error with hydra 4.5 on CentOS, and it never got solved. I also added the ppalaunchpad repository that says there are precompiled .deb packages for hydra and hydra-gtk. The repository loaded fine, was detected fine, there were no errors when I hit reload in Synaptic...but no hydra packages are found when I search. Anyway, THC Hydra is a very powerful pentesting tool that I think would be a great addition to the toolkit I'm making. Does anyone know how I might get this installed? Below is the whole output (from ./configure to sudo make install of hydra)


chris@HOSTNAME:~/thorn stuff/to be installed/hydra-5.4-src$ ./configure 

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from [http://0xbadc0de.be/](http://0xbadc0de.be/) - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
chris@HOSTNAME:~/thorn stuff/to be installed/hydra-5.4-src$ make
cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
Error: could not compile. Analyse this:
callbacks.c: In function &#8216;popen_re_unbuffered&#8217;:
callbacks.c:532: warning: format not a string literal and no format arguments
callbacks.c: In function &#8216;on_btnSave_clicked&#8217;:
callbacks.c:668: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
In function &#8216;open&#8217;,
    inlined from &#8216;on_btnSave_clicked&#8217; at callbacks.c:666:
/usr/include/bits/fcntl2.h:51: error: call to &#8216;__open_missing_mode&#8217; declared with attribute error: open with O_CREAT in second argument needs 3 arguments
In function &#8216;snprintf&#8217;,
    inlined from &#8216;hydra_get_options&#8217; at callbacks.c:247:
/usr/include/bits/stdio2.h:65: warning: call to __builtin___snprintf_chk will always overflow destination buffer
make[3]: *** [callbacks.o] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive-am] Error 2

Do not worry, as I said, xhydra is really optional. ./hydra is ready to go!

Now type make install
chris@HOSTNAME:~/thorn stuff/to be installed/hydra-5.4-src$ sudo make install
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)

---

### Post by computerjunkie on 2009-03-09
Ok, so I looked at the config, is it the libssh and the sapr3 modules that are causing this? if so, why does it say hydra is "ready to go"? so in case it was those modules, I downloaded libssh 0.11 and got that installed. I followed the link to sapr3 and uh, where is the download for it. It's just a website selling enterprise editions of netweaver.

Any help would be greatly appreciated

P.S. I'm assuming this isn't it: [http://linux.softpedia.com/progDownload/SAP-R-3-Communications-Suite-Download-15771.html](http://linux.softpedia.com/progDownload/SAP-R-3-Communications-Suite-Download-15771.html) 

That is a 28+MB download with a bunch of .jar files. Is that what hydra is looking for? if so, where are the makefiles and install instructions?

The THC hydra website doesn't even come up, is this project dead and buried? I still don't understand why the ppalaunchpad repo didn't work out right, as I mentioned in my last post. here is the repo link:

deb [http://ppa.launchpad.net/hydra-packages/ppa/ubuntu](http://ppa.launchpad.net/hydra-packages/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/hydra-packages/ppa/ubuntu](http://ppa.launchpad.net/hydra-packages/ppa/ubuntu) intrepid main (source code)

I found the information here: [https://launchpad.net/~hydra-packages/+archive/ppa](https://launchpad.net/~hydra-packages/+archive/ppa)

I also tried following the instructions located here: [http://www.wiredbytes.com/node/7](http://www.wiredbytes.com/node/7)  also, to no avail.

Why is this so hard to install?

---

### Post by computerjunkie on 2009-03-09
~bump~

---

### Post by chronos00 on 2009-07-17
I found a very simple answer today, by simply downloadong the THC-Hydra's .deb from Backtrack's repository.
[http://repo.offensive-security.com/dist/bt4/binary/]("http://repo.offensive-security.com/dist/bt4/binary/")
[http://repo.offensive-security.com/dist/bt4/binary/hydra.deb]("http://repo.offensive-security.com/dist/bt4/binary/hydra.deb")
As a matter of fact, I guess you could even add the whole BackTrack repository to your Ubuntu installation.

---

### Post by chronos00 on 2009-07-17
Some more info:

The .deb you will find in the Backtrack's repo won't have SSH2 support compiled in the binary. So... I guess it will not be that easy.
Anyway, y found this thread in their forum, asking for just that, and many people explained how they managed to compile Hydra. Read every post, because there is useful information in every one (the last post did the trick for me :)
[http://forums.remote-exploit.org/bt4beta-bugs-fixes/21101-fix-hydra.html]("http://forums.remote-exploit.org/bt4beta-bugs-fixes/21101-fix-hydra.html")

---

### Post by equusaustralus on 2010-01-13
Thanx chronos00, the .deb worked for me, had similar problems with the compilation from source! ;)

---

### Post by oxidizer on 2010-05-24
I have same problem I'm using Ubuntu 10.04 Is there any perfect solution i used "make Install" and "check install" but same Error of _computerjunkie_

---

### Post by henyongadik01 on 2010-07-20
Hi. Im trying to install this to ubuntu 10.04 64-bit

> [http://freeworld.thc.org/thc-hydra/README](http://freeworld.thc.org/thc-hydra/README)However, it doesnt let me:

> ubuntu02@ubuntu02:~/Desktop/ubuntu02/hydra-5.7-src$ sudo ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... NOT found, SSL support disabled
Get it from [http://www.openssl.org](http://www.openssl.org)
Checking for Postgres (libpq.so) ...
                                 ... NOT found, module postgres disabled
Checking for SVN (libsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... NOT found, module svn disabled
Checking for firebird (libfbclient.so) ...
                                       ... NOT found, module firebird disabled
Checking for NCP (libncp.so / nwcalls.h) ...
                                         ... NOT found, module NCP disabled
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from [http://www.libssh.org](http://www.libssh.org)
Checking for GUI req's (pkg-config) ...
                                    ... found

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...
now type "make"
ubuntu02@ubuntu02:~/Desktop/ubuntu02/hydra-5.7-src$ sudo make
gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
gcc -I. -Wall -O2 -c hydra-vnc.c  
gcc -I. -Wall -O2 -c hydra-pcnfs.c  
gcc -I. -Wall -O2 -c hydra-rexec.c  
gcc -I. -Wall -O2 -c hydra-nntp.c  
gcc -I. -Wall -O2 -c hydra-socks5.c  
gcc -I. -Wall -O2 -c hydra-telnet.c  
gcc -I. -Wall -O2 -c hydra-cisco.c  
gcc -I. -Wall -O2 -c hydra-http.c  
gcc -I. -Wall -O2 -c hydra-ftp.c  
gcc -I. -Wall -O2 -c hydra-imap.c  
gcc -I. -Wall -O2 -c hydra-pop3.c  
gcc -I. -Wall -O2 -c hydra-smb.c  
gcc -I. -Wall -O2 -c hydra-icq.c  
gcc -I. -Wall -O2 -c hydra-cisco-enable.c  
gcc -I. -Wall -O2 -c hydra-ldap.c  
gcc -I. -Wall -O2 -c hydra-mysql.c  
gcc -I. -Wall -O2 -c hydra-http-proxy.c  
gcc -I. -Wall -O2 -c hydra-smbnt.c  
gcc -I. -Wall -O2 -c hydra-mssql.c  
gcc -I. -Wall -O2 -c hydra-snmp.c  
gcc -I. -Wall -O2 -c hydra-cvs.c  
gcc -I. -Wall -O2 -c hydra-smtpauth.c  
gcc -I. -Wall -O2 -c hydra-sapr3.c  
gcc -I. -Wall -O2 -c hydra-ssh2.c  
gcc -I. -Wall -O2 -c hydra-teamspeak.c  
In file included from /usr/include/string.h:640,
                 from hydra.h:5,
                 from hydra-mod.h:8,
                 from hydra-teamspeak.c:1:
In function ‘strcpy’,
    inlined from ‘start_teamspeak’ at hydra-teamspeak.c:45:
/usr/include/bits/string3.h:107: warning: call to __builtin___strcpy_chk will always overflow destination buffer
gcc -I. -Wall -O2 -c hydra-postgres.c  
gcc -I. -Wall -O2 -c hydra-rsh.c  
gcc -I. -Wall -O2 -c hydra-rlogin.c  
gcc -I. -Wall -O2 -c hydra-oracle-listener.c  
hydra-oracle-listener.c:10:2: warning: #warning "The Oracle Listener module does not work yet"
gcc -I. -Wall -O2 -c hydra-svn.c  
gcc -I. -Wall -O2 -c hydra-pcanywhere.c  
gcc -I. -Wall -O2 -c hydra-sip.c  
hydra-sip.c: In function ‘dummy_sip’:
hydra-sip.c:8: warning: implicit declaration of function ‘printf’
hydra-sip.c:8: warning: incompatible implicit declaration of built-in function ‘printf’
gcc -I. -Wall -O2 -c hydra-vmauthd.c  
gcc -I. -Wall -O2 -c hydra-smtpauth-ntlm.c  
hydra-smtpauth-ntlm.c: In function ‘start_smtpauth_ntlm’:
hydra-smtpauth-ntlm.c:33: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-smtpauth-ntlm.c:33: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-smtpauth-ntlm.c:51: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-smtpauth-ntlm.c:51: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -I. -Wall -O2 -c hydra-firebird.c  
gcc -I. -Wall -O2 -c hydra-ncp.c  
gcc -I. -Wall -O2 -c hydra-http-proxy-auth-ntlm.c  
hydra-http-proxy-auth-ntlm.c: In function ‘start_http_proxy_auth_ntlm’:
hydra-http-proxy-auth-ntlm.c:50: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-http-proxy-auth-ntlm.c:50: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-http-proxy-auth-ntlm.c:68: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-http-proxy-auth-ntlm.c:68: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -I. -Wall -O2 -c hydra-imap-ntlm.c  
hydra-imap-ntlm.c: In function ‘start_imap_ntlm’:
hydra-imap-ntlm.c:41: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-imap-ntlm.c:41: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-imap-ntlm.c:52: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-imap-ntlm.c:52: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -I. -Wall -O2 -c hydra-pop3-ntlm.c  
hydra-pop3-ntlm.c: In function ‘start_pop3_ntlm’:
hydra-pop3-ntlm.c:40: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-pop3-ntlm.c:40: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-pop3-ntlm.c:51: warning: dereferencing type-punned pointer will break strict-aliasing rules
hydra-pop3-ntlm.c:51: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -I. -Wall -O2 -c hydra-http-form.c  
hydra-http-form.c: In function ‘start_http_form’:
hydra-http-form.c:119: warning: format ‘%d’ expects type ‘int’, but argument 9 has type ‘size_t’
hydra-http-form.c:131: warning: format ‘%d’ expects type ‘int’, but argument 8 has type ‘size_t’
hydra-http-form.c:142: warning: format ‘%d’ expects type ‘int’, but argument 6 has type ‘size_t’
gcc -I. -Wall -O2 -c crc32.c  
gcc -I. -Wall -O2 -c d3des.c  
gcc -I. -Wall -O2 -c md4.c  
gcc -I. -Wall -O2 -c hydra-mod.c  
gcc -I. -Wall -O2 -c ntlm.c  
gcc -I. -Wall -O2 -c hydra.c  
hydra.c: In function ‘hydra_restore_write’:
hydra.c:335: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
hydra.c:335: warning: format ‘%d’ expects type ‘int’, but argument 5 has type ‘long int’
gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-vmauthd.o hydra-smtpauth-ntlm.o hydra-firebird.o hydra-ncp.o hydra-http-proxy-auth-ntlm.o hydra-imap-ntlm.o hydra-pop3-ntlm.o hydra-http-form.o crc32.o d3des.o md4.o hydra-mod.o ntlm.o hydra.o -lm  

If men could get pregnant, abortion would be a sacrament

cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
`src/xhydra' -> `../xhydra'
The GTK GUI is ready, type "./xhydra" to start

Now type make install
ubuntu02@ubuntu02:~/Desktop/ubuntu02/hydra-5.7-src$ sudo make install
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
cp: target `/usr/local/bin' is not a directory
make: [install] Error 1 (ignored)
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
cd: 1: can't cd to /usr/local/bin
make: [install] Error 2 (ignored)
i think hydra is an interesting application. Anyone here successfully installed hydra? Anyone can help with errors? Thanks.

---

### Post by david.maciejak on 2010-10-19
did you try v5.8 ? [http://freeworld.thc.org/thc-hydra/](http://freeworld.thc.org/thc-hydra/)
and installing missing libraries ?

---

### Post by joseramos07 on 2011-02-13
Hi;

     I installed it easily in 10.04, I leave here the steps I made:

1- Download [http://freeworld.thc.org/releases/hydra-6.1-src.tar.gz](http://freeworld.thc.org/releases/hydra-6.1-src.tar.gz)
2- tar -xvzf hydra-6.1-src.tar.gz
3- cd  hydra-6.1-src/
4- ./configure
5- make
6- sudo make install
and use
7- xhydra

I hope you work correctly, if problems do not hesitate to contact me.


Jose Carlos Ramos Carmenates
[email]jramoscarmenates@gmail.com[/email]
Saludos

---

### Post by chronos00 on 2011-02-14
It's very nice to see the hydra project is still alive and kicking.

Thanks for your insights Jose!
Regards from Argentina.

---

