---
title: "Evolution-mapi, authentication and mailbox in different servers"
date: 2011-05-10
forum: Desktop Environments
---

### Post by enid on 2011-05-10
Hello to all,
Since in my work environment I'm forced to use the exchange server as mail service :( , I found that evolution had this great plugin (evolution-mapi) which allowed me to connect to exchange 2003 server from evolution mail client.

I'm using Ubuntu 10.10 and: 
# dpkg -l |grep evolution
ii  evolution                                     2.30.3-1ubuntu6                                 
ii  evolution-common                              2.30.3-1ubuntu6                   
ii  evolution-couchdb                             0.5.0-0ubuntu1                   
ii  evolution-data-server                         2.30.3-2ubuntu1              
ii  evolution-data-server-common                  2.30.3-2ubuntu1      
ii  evolution-exchange                            2.30.3-0ubuntu1               
ii  evolution-indicator                           0.2.10-0ubuntu1                  
ii  evolution-mapi                                0.30.3-1ubuntu1                   
ii  evolution-plugins                             2.30.3-1ubuntu6                 
ii  evolution-webcal                              2.28.1-1



Everything went fine when was used only one server both for Active Directory (authentication) and mailbox storage (exchange).

But after some architecture changes the AD service and exchange service now run on different machines, so on evolution plugin (create new account, server type -> exchange mapi) I get only one address/ip to enter both for authentication and mailbox.
If I enter the AD ip, I get authenticated but the evolution client crashes with some error logs "kernel: [ 5247.756268] evolution[6361]: segfault at 14 ip 030787da sp bfa483c0 error 4 in libgensec.so.0.0.1[2e37000+324000]"

and if I enter the mailbox server ip I get "Authentication failed.
MapiLogonProvider:MAPI_E_NETWORK_ERROR" if I enter the correct username pass, and "Authentication failed. MapiLogonProvider:MAPI_E_LOGON_FAILED" if I enter some wrong user/pass. 

Has this happened to anyone, and does evolution-mapi plugin in some way solve this part, in how to connect to exchange server.
I do not want to switch to M$ windoze , and Outloo(uc)k . :P

Thanks

---

### Post by digitallife on 2012-01-09
<to delete>

---

