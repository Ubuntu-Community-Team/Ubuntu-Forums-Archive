---
title: "Citrix HowTo"
date: 2005-10-25
forum: Desktop Environments
---

### Post by marguz on 2005-10-25
All,

Citrix ICA client 9.0 works fine in Ubuntu Breezy connecting to either Windows 2000 or Windows 2003 servers running Citrix XP versions and up.

What I did was:
ln -s /usr/X11R6/lib/libXm.so.3.0.2 /usr/lib/libXm.so.3

That link was done AFTER I ran the Automatix script, so I do not know if /usr/X11R6/lib/libXm.so.3.0.2 is there with a fresh Breezy install.

I hope that this helps :-)

---

### Post by aubuti on 2005-10-25
Thanks for the tip, but it's no help for me. When I tried to set the link I got the following:

~/> sudo ln -s /usr/X11R6/lib/libXm.so.3.0.2 /usr/lib/libXm.so.3
Password:
ln: `/usr/lib/libXm.so.3': File exists

and indeed it does.

I'm on Breezy with the Citrix 9 client, trying to log onto a Windows 2000 Terminal Server. Whether I run wfica or wfcmgr I get as far as the server's login screen, but then I can't type in my username or password, or click anywhere in the window. Once I move into the window area the cursor turns from an arrow to a grey vertical line. 

The specific error messages are:
~/> sudo /usr/lib/ICAClient/wfica
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
*** glibc detected *** double free or corruption (!prev): 0x082e6d90 ***
Aborted

~/> sudo /usr/lib/ICAClient/wfcmgr
Warning: locale not supported by C library, locale unchanged
Warning: locale not supported by C library, locale unchanged

Any clues out there? Thanks in advance.

-Ken

---

### Post by marguz on 2005-10-25
So,

Are you able to connect to that Citrix server via RDP?
Are you able to connect to that Citrix server from a Windows client?

What version of Citrix is it? Are you the admin?

---

### Post by ltmon on 2005-10-26
[QUOTE=aubuti]Thanks for the tip, but it's no help for me. When I tried to set the link I got the following:

~/> sudo ln -s /usr/X11R6/lib/libXm.so.3.0.2 /usr/lib/libXm.so.3
Password:
ln: `/usr/lib/libXm.so.3': File exists

and indeed it does.

I'm on Breezy with the Citrix 9 client, trying to log onto a Windows 2000 Terminal Server. Whether I run wfica or wfcmgr I get as far as the server's login screen, but then I can't type in my username or password, or click anywhere in the window. Once I move into the window area the cursor turns from an arrow to a grey vertical line. 

The specific error messages are:
~/> sudo /usr/lib/ICAClient/wfica
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
*** glibc detected *** double free or corruption (!prev): 0x082e6d90 ***
Aborted

~/> sudo /usr/lib/ICAClient/wfcmgr
Warning: locale not supported by C library, locale unchanged
Warning: locale not supported by C library, locale unchanged

Any clues out there? Thanks in advance.

-Ken[/QUOTE]

Have you tried installing the package msttcorefonts?

I had a very similar problem in wine (everything worked, but no text was displayed) until I installed this package.

L.

---

### Post by wawa on 2005-12-07
I dont think /usr/X11R6/lib/libXm.so.3.0.2 comes with fresh breezy install, I had to install libmotif3

---

### Post by Didjit on 2006-01-12
Just installed Ubuntu, trying to get some key apps up like Citix. The guide was great, but I'm getting this error: you have chosen not to
trust "Entrust.net Secure Server Certification Authority", the issuer of the
server's security certificate'  

Is there a cert I need to install?? (Sorry, work help desk does not support *nix. Doesn't happen w/windoze....)

Hope this thread didn't go stale.....

Chris

---

### Post by RU63 on 2006-01-12
I am getting the same error as you 'Didjit'
and I am in the same situation, no support from IT.

Perhaps we should start a new thread?

---

### Post by bensode on 2006-01-12
Citrix server runs on top of Windows Terminal Services.  You should be able to RDP into these servers without using the citrix client, however, you must make sure that your terminal services are properly licensed.  A common mistake people don't understand is that even though you bought Citrix licenses you are still required to license TS clients.  The whole reason I dumped Citrix and just run MS Server 2003 Terminal Services. ;) 

Anywho, make sure that you can RDP into the Citrix server at the least.

---

### Post by Didjit on 2006-01-13
[QUOTE=Didjit] 

Is there a cert I need to install?? (Sorry, work help desk does not support *nix. Doesn't happen w/windoze....)
[/QUOTE]

K, got a little further. Our IT did post info for using a OSX (Mac) and yes, I need to install a certificate. Problem is it is a .pkg file (guess this is an OSX package?). Is there a deb conversion utility (like Alien) so I can convert the .pkg to something Ubuntu will know? 

Chris

---

### Post by Didjit on 2006-01-19
Download the Entrust Root certificate
   * Available from : [http://www.entrust.net/downloads/binary/entrust_ssl_ca.cer](http://www.entrust.net/downloads/binary/entrust_ssl_ca.cer) 
 * Save it as: /usr/lib/ICAClient/keystore/cacerts/entrust_ssl_ca.crt
   * note the extension change here!

Found this. Citrix is now working for me!! This should help you too **RU63.**

Chris

---

### Post by Narrf on 2006-02-03
I had a similar problem with Thawte certificates, where the ICA client refused to connect displaying the error: "You have not chosen to "Thawte Premium Server CA", the issuer of the server's security certificate."

I found the Thwate root certs by registering at [http://www.thawte.com/roots/]("http://www.thawte.com/roots/") and downloading the .zip file. Extracting, renaming and placing the CA Root cert in /usr/lib/ICAClient/keystore/cacerts sorted the problem, as Chris recommended.

Cheers
Stuart

---

### Post by ericsp on 2006-02-05
thanks. I managed to fix it indeed by using the relevant certificate and follow the instructions. btw I did this under **Dapper Flight 3 **(with all updates). There was one command that did not work for me but did not hamper functionality. Here is what I did:

[LIST=1]
[*]apt-get install libxaw6 libmotif3
[*]ln -s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3
[*]apt-get install alien
[*]sudo alien ICAClient-9.0-1.i386.rpm
[*]dpkg -i icaclient_9.0-2_i386.deb
[*]wget [http://secure.globalsign.net/cacert/Root.crt](http://secure.globalsign.net/cacert/Root.crt)
[*]cp Root.crt /usr/lib/ICAClient/keystore/cacerts/entrust_ssl_ca.crt
[/LIST]

when opening associate the "launch.asp" with "/usr/lib/ICAClient/wfica.sh"

Then everything worked perfectly!

---

### Post by ericsp on 2006-02-06
I want to run the client in a window and not full screen. Does anyone know the option? 
*./wfica.sh* -help did not list the option.

Thanks
Eric

---

