---
title: "gnucash, american express, and ofx direct connect"
date: 2009-03-22
forum: General Help
---

### Post by thenanodude on 2009-03-22
Try as i might, I cannot get gnucash to download my transactions from American Express!  I have been able to get it to connect to my bank and to my Citibank credit card.  

First question:  can anybody who has been able to successfully download from American Express post the relevant sections from ~/.aqbanking/settings.conf?

Second question: does anybody have any suggestions?!  Here is some info:

I'm running xubuntu 8.04 (hardy) on an AMD 64
gncuash version: 2.2.9 
aqbanking version: 3.5.1-1

I installed the .deb packages of gnucash from [http://www.getdeb.net/](http://www.getdeb.net/)
I got the aqbanking by adding the repositories from [https://launchpad.net/~gnucash/+archive/ppa](https://launchpad.net/~gnucash/+archive/ppa)

I had originally installed gnucash 2.2.6 from the ppa.launchpad.net site, but I could not get any of my credit cards to work.  after updating to 2.2.9, I can get Citibank, but still not American Express.

I am using ORG=AMEX
FID=3101
URL=https://www99.americanexpress.com/myca/ofxdl/us/download?request_type=nl_desktopdownload 

(these values are from [http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings](http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings)


I am unable to get the AqBanking Wizard to Get Accounts correctly when I have entered the user information.  I get the error "Network error while waiting for response" and the following in /tmp/gnucash.trace:

> * 19-01-50:aqbanking(27057):qbanking.cpp:  420: No Qt translation found for your language en
* 19-02-30: (null)(27057):network.c:  397: Saving response in "/tmp/ofx.log" ...
* 19-02-31:qt3_wizard(27057):cppgui.cpp:  522: Checking cert
* 19-02-34:gwen(27057):io_tls.c:  939: gnutls_record_recv: -9 (A TLS packet with unexpected length was received.) [decoding 801 bytes]
* 19-02-34:gwen(27057):io_tls.c: 1217: gnutls_bye: -10 (The specified session has been invalidated for some reason.)
* 19-02-34: (null)(27057): provider.c:  659: Error exchanging getAccounts-request (-103)
* 19-02-34:qt3_wizard(27057):cfgtabpageuserofx.cpp:  283: Error requesting account list



so I tried manually installing the account, but to no avail.  I then tried manually editing ~/.aqbanking/settings.conf.  Here are my relevant sections:

>   user {
    int  uniqueId="8"
    char backendName="aqofxconnect"
    char userName="xxxxxx"
    char userId="xxxxxx"
    char customerId="xxxxxx"
    char country="US"
    char bankCode="AMEX"
    int  lastSessionId="0"

    data {
      backend {
        char fid="3101"
        char org="AMEX"
        char appid="QWIN"
        char appver="1400"
        char serverType="https"
        char serverAddr="https%3A%2F%2Fwww99.americanexpress.com%2Fmyca%2Fofxdl%2Fus%2Fdownload?request%5Ftype%3Dnl%5Fdesktopdownload "
        char headerver="102"
        char flags="account%5Flist", "statements", "forceSsl3"
      } #backend
    } #data
  } #user

  account {
    int  uniqueId="60"
    char country="US"
    char bankCode="AMEX"
    char accountNumber="XXXXXXXXXXXXXXXX"
    int  user="8"
    char bankName="AMEX"
    int  accountType="2"
    char accountName="Amex Gold"
    char provider="aqofxconnect"
  } #account


When I do "Actions-->Online Actions-->Get transactions" a box pops up with the following messages (at some point I am asked to enter my password and to accept a certificate, which I do):

> Sending jobs to the bank(s)
Saving communication log to /tmp/ofx.log
Resolving hostname "www99.americanexpress.com" ...
IP address is 12.29.100.25
Sending request...
Connecting to bank...
Connected.
Waiting for response...
Network error while waiting for response
Error parsing server response
Postprocessing jobs
Resetting provider queues



with the following in /tmp/gnucash.trace:

> * 19:10:08  CRIT <aqofxconnect> network.c:  397: Saving response in "/tmp/ofx.log" ...
* 19:10:11  CRIT <gwenhywfar> io_tls.c:  939: gnutls_record_recv: -9 (A TLS packet with unexpected length was received.) [decoding 114 bytes]
* 19:10:12  CRIT <gwenhywfar> io_tls.c: 1217: gnutls_bye: -10 (The specified session has been invalidated for some reason.)
* 19:10:12  CRIT <aqofxconnect> provider.c:  783: Error exchanging getStatements-request (-103)




with env variable AQOFX_LOG_COMM=1, I receive the following in /tmp/ofx.log (I have XX'd out my user, pass, and account name):


> Sending:
-------------------------------------
OFXHEADER:100
DATA:OFXSGML
VERSION:102
SECURITY:NONE
ENCODING:USASCII
CHARSET:1252
COMPRESSION:NONE
OLDFILEUID:NONE
NEWFILEUID:20090322154830.000

<OFX><SIGNONMSGSRQV1><SONRQ><DTCLIENT>20090322154830.000
<USERID>XXXXXX
<USERPASS>XXXXXX
<LANGUAGE>ENG
<FI><ORG>AMEX<FID>3101</FI>
<APPID>QWIN<APPVER>1400
</SONRQ></SIGNONMSGSRQV1>
<CREDITCARDMSGSRQV1><CCSTMTTRNRQ>
 <TRNUID>20090322154830.000
 <CLTCOOKIE>1
 <CCSTMTRQ>
   <CCACCTFROM><ACCTID>XXXXXXXXXXXXXXXX</CCACCTFROM>
   <INCTRAN><DTEND>20090322154828<INCLUDE>Y</INCTRAN>
 </CCSTMTRQ>
</CCSTMTTRNRQ></CREDITCARDMSGSRQV1></OFX>




I've tried all the things I could think of, including checking and unchecking various boxes in the AqBanking wizard (e.g. ForceSsl3, Send blank bank ID).  

Any help would be appreciated!!!

---

### Post by thenanodude on 2009-03-29
Please?  anybody?  any suggestions?

---

### Post by tedtlogan on 2009-05-16
I will try to help you, but please help me and others as well.  Please paste your relevant sections for citibank credit card, as I have not been able to get the settings for that.


Under users for online banking setup for citibank i have

user name: firstlast
user id: firstlast
customer id: firstlast

country: U.S.
bank ID: 24909 - I'M SURE THIS IS WRONG, CAN YOU PLEASE TELL ME WHAT IT IS?

under OFX tab
FID: 24909
ORG: Citigroup

URL: [https://secureofx2.bankhost.com/citi/cgi-forte/ofx_rt?servicename=ofx_rt&pagename=ofx](https://secureofx2.bankhost.com/citi/cgi-forte/ofx_rt?servicename=ofx_rt&pagename=ofx)

support accounts list download, supports statements download:

I then click get accounts, and I put password, and a screen pops up then quickly closes.

Please let me know what you have different here, thanks!

---

### Post by thenanodude on 2009-05-19
> Please paste your relevant sections for citibank credit card, as I have not been able to get the settings for that.

Under users for online banking setup for citibank i have

  <snip>

bank ID: 24909 - I'M SURE THIS IS WRONG, CAN YOU PLEASE TELL ME WHAT IT IS?



For "Bank ID" I have "Citigroup" although I'm not sure it matters.

> 
under OFX tab
FID: 24909
ORG: Citigroup

URL: [https://secureofx2.bankhost.com/citi...t&pagename=ofx](https://secureofx2.bankhost.com/citi...t&pagename=ofx)

support accounts list download, supports statements download:




try checking the "Force SSLv3" box.  I think this may be important.

Otherwise, may settings are all the same.  One note:  these are for the Citibank credit cards.  There may be different settings for the bank accounts (checking, savings, etc.)


One more thing worth checking:  in ".aqbanking/setting.cof" the relevant account{} section for the Citibank card may need the line:

 int  accountType="2"

---

### Post by ccd on 2009-06-02
Hello thenanodude,

I have the exact same problem as you. Citi credit card is working but amex is not. Did you make any progress dealing with amex?

BTW, I am running debian/stable
gnucash: 2.2.6-2 from stable
aqbanking: 3.8.2-1 from testing (v3.6.2-1/stable has a bug [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505509](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505509))

Thanks,
- ccd

---

### Post by thenanodude on 2009-06-08
> **ccd said:**
> 

I have the exact same problem as you. Citi credit card is working but amex is not. Did you make any progress dealing with amex?



No, still haven't made any progress.  I have just been going to the Amex site and downloading my transactions as a .ofx.  I have exhausted everything I know to do.  if anybody has any tips, they would be appreciated!

---

### Post by Cuba71 on 2009-08-04
> **thenanodude said:**
> No, still haven't made any progress.  I have just been going to the Amex site and downloading my transactions as a .ofx.  I have exhausted everything I know to do.  if anybody has any tips, they would be appreciated!

Your post is a couple of months old, let me know if you're still having problems configuring AMEX

---

### Post by thenanodude on 2009-08-06
I am still having problems.  However, I upgraded to Jaunty and the latest versions of aqbanking and gnucash availabe under Jaunty, and now none of the online banking works.  I haven't had time to try to fix it yet, but I still welcome any suggestions!

---

### Post by thenanodude on 2009-08-07
I think I finally figured it out!!  My problem seemed to be that I was sending an outdated or blank "appVer" number.  I found updated numbers here:
[http://ofxblog.wordpress.com/2007/06/06/ofx-appid-and-appver-for-intuit-products/](http://ofxblog.wordpress.com/2007/06/06/ofx-appid-and-appver-for-intuit-products/)

below are the relevant sections from ~/.aqbanking/settings.conf  (note that I have X'd out any information that is either irrelevant or private, so you'll want to change these in your own settings.conf):

```

users {

{snip}....

  user {
    int  uniqueId="XXX"
    char backendName="aqofxconnect"
    char userName="XXX"
    char userId="XXXX"
    char customerId="XXXX"
    char country="US"
    char bankCode="AMEX"
    int  lastSessionId="0"

    data {
      backend {
        char flags="statements", "forceSsl3"
        char org="AMEX"
        char fid="3101"
        char serverType="https"
        char serverAddr="https%3A%2F%2Fwww99.americanexpress.com%2Fmyca%2Fofxdl%2Fus%2Fdownload?request%5Ftype%3Dnl%5Fdesktopdownload"
        int  serverPort="0"
        char appId="QWIN"
        char appVer="1700"
        char headerVer="102"
      } #backend
    } #data
  } #user

{snip}....

} #users

accounts {

{snip}.....

  account {
    char provider="aqofxconnect"
    int  uniqueId="147"
    int  accountType="2"
    char accountNumber="XXXX"
    char accountName="XXX"
    char bankName="AMEX"
    char ownerName="XXXX"
    char currency="EUR"
    char country="US"
    int  user="141"
    int  selectedUser="xxx

    apps {
    } #apps

    provider {
      int  maxPurposeLines="1"
      int  debitAllowed="0"
    } #provider
  } #account

{snip}....

} #accounts

```


For the record, I have the following packages installed under Jaunty:

aqbanking-tools                            3.7.2-1
libaqbanking-data                          3.7.2-1                                   
libaqbanking-plugins-libgwenhywfar47       3.7.2-1
libaqbanking20                             3.7.2-1
libaqbanking20-plugins                     3.7.2-1
libaqbanking20-plugins-qt                  3.7.2-1  
gnucash                                    2.2.9-1~getdeb1
gnucash-common                             2.2.9-1~getdeb

---

