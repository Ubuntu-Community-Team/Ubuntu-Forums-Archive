---
title: "Login with kerberos user on ubuntu 16.04 Desktop with sudo privileges"
date: 2019-03-23
forum: Desktop Environments
---

### Post by jayram1989 on 2019-03-23
I'm setting up a lab, in this case we have few ubuntu 16.04 Desktop, in that I'm planning to login with kerberos user with sudo privileges. It means, whenever a new user login to this desktop with his kerberos creds, a home directory will create and he will get sudo privileges for this machine. 


Env:- 
16.04.4 LTS (Xenial Xerus)"
4.13.0-36-generic




In my case user=test , domain = AD.TEST.EDU hostname = test.com 


Added in /etc/pam.d/common-session for enabling home directory


    session    optional            pam_mkhomedir.so skel=/etc/skel/ umask=0077 
    # end of pam-auth-update config


Regarding to enable sudo for these kerberos users, I couldn't find the info using "id" command


    #id ad.test.edu\\test
     id: ‘ad.test.edu\\test’: no such user


But here klist shows fine. How can I add rule for these kerberos user in sudo list? 


Below is the krb client configuration. 


        $grep -i  ad.te /etc/krb5.conf 
        kdc = ad.test.edu
        admin_server = ad.test.edu


I'm able to get the kerberos ticket without any issues 


    $kinit [EMAIL="test@AD.TEST.EDU"]test@AD.TEST.EDU[/EMAIL]
     Password for [EMAIL="test@AD.TEST.EDU"]test@AD.TEST.EDU[/EMAIL]: 


Below is the ticket details


     $klist 
     Ticket cache: FILE:/tmp/krb5cc_1000
     Default principal: [EMAIL="test@AD.TEST.EDU"]test@AD.TEST.EDU[/EMAIL]


       Valid starting       Expires              Service principal
       03/20/2019 09:36:05  03/21/2019 02:36:05  
     krbtgt/AD.TEST.EDU@AD.TEST.EDU




Even from console, I'm able to retrieve tickets without any issues 


 


    Mar 20 10:09:58 TEST lightdm: pam_krb5(lightdm:auth): user [EMAIL="test@AD.TEST.EDU"]test@AD.TEST.EDU[/EMAIL] authenticated as [EMAIL="test@AD.TEST.EDU"]test@AD.TEST.EDU[/EMAIL]
    Mar 20 10:09:58 TEST  lightdm: gkr-pam: error looking up user information
    Mar 20 10:09:58 TEST  lightdm: pam_kwallet5(lightdm:auth): (null): pam_sm_authenticate
    Mar 20 10:09:58 TEST  lightdm: pam_kwallet5(lightdm:auth): pam_kwallet5: Couldn't get user info (passwd) info
    Mar 20 10:09:58 TEST  lightdm: pam_unix(lightdm:account): could not identify user (from getpwnam(test@AD.TEST.EDU))
    Mar 20 10:09:58 TEST  lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
    Mar 20 10:09:58 TEST  lightdm: PAM adding faulty module: pam_kwallet.so


Here I thought, below entry causing problem, by eliminate this install this package - libpam-kwallet5 . But after that, once I login with local user, I'm unable to logout from the session, It takes 3 or 4 times try to hit the logout button. After removing this package - libpam-kwallet5 , there is no issue. 


    Mar 20 10:09:58 TEST lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory




I tried with kerberos user name syntax as "test@AD.TEST.EDU" , "test/AD.TEST.EDU" , test/AD.TEST.EDU@AD.TEST.EDU. Nothing help here. 




    Mar 20 10:14:35 TEST lightdm: pam_krb5(lightdm:auth): user [EMAIL="test@AD.TEST.EDU"]test@AD.TEST.EDU[/EMAIL] authenticated as [EMAIL="test@AD.TEST.EDU"]test@AD.TEST.EDU[/EMAIL]
    Mar 20 10:14:35 TEST lightdm: gkr-pam: error looking up user information
    Mar 20 10:14:35 TEST lightdm: pam_kwallet(lightdm:auth): (null): pam_sm_authenticate
    Mar 20 10:14:35 TEST lightdm: pam_kwallet(lightdm:auth): pam_kwallet: Couldn't get user info (passwd) info
    Mar 20 10:14:35 TEST lightdm: pam_kwallet5(lightdm:auth): (null): pam_sm_authenticate
    Mar 20 10:14:35 TEST lightdm: pam_kwallet5(lightdm:auth): pam_kwallet5: Couldn't get user info (passwd) info
    Mar 20 10:14:35 TEST lightdm: pam_unix(lightdm:account): could not identify user (from getpwnam(test@AD.TEST.EDU))




Here I want to acheive below three things


1) Login to Ubuntu desktop using kerberos user


2) Create home directory for login user


3) Provide sudo privileges for the login user. 


Comment me some suggestions. 


Thanks

---

