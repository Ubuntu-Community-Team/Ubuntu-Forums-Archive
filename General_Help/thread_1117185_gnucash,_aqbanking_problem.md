---
title: "gnucash, aqbanking problem"
date: 2009-04-05
forum: General Help
---

### Post by harphauler on 2009-04-05
Hi,

Ubuntu 8.10; Gnucash 2.2.6; aqbanking aqofxconnect backend 3.5.1

I'm oh so close to being able to give up the windoze habit and am halfway there with gnucash.  I am able to use the online banking with Wells Fargo just fine and dandy.  Then was so proud to find what I believe to be correct OFX settings for Wachovia Securities (note it's not the bank but the securities side; info in the logs below.)

I am able to "Get Accounts" in the aqbanking setup walk-thru.  Then have set up the different accounts as I did for Wells Fargo.  However when it's time to download transactions, (from earliest possible date option) I get a response of The Online Banking import returned no transactions for the selected time period.

Any help gratefully appreciated.  Here's info from the gnucash.trace file and the ofx.tmp files for two attempts at getting transactions:

gnucash.trace:
* 16:03:23  CRIT <aqofxconnect> network.c:  397: Saving response in "/tmp/ofx.log" ...
* 16:03:26  CRIT <aqofxconnect> network.c:  491: Saving response in "/tmp/ofx.log" ...
* 16:03:29  WARN <gnc.import.aqbanking> bal_accountinfo_cb: noted_bal == NULL.  Assuming 0
* 16:03:51  CRIT <aqofxconnect> network.c:  397: Saving response in "/tmp/ofx.log" ...
* 16:03:51  CRIT <aqofxconnect> network.c:  491: Saving response in "/tmp/ofx.log" ...
* 16:03:54  WARN <gnc.import.aqbanking> bal_accountinfo_cb: noted_bal == NULL.  Assuming 0
* 16:04:27  CRIT <aqofxconnect> network.c:  397: Saving response in "/tmp/ofx.log" ...
* 16:04:59  CRIT <aqofxconnect> network.c:  343: Got an error response (500: <BODY><H1>Server Error</H1>Error while processing request by OFX server</BODY>)
* 16:04:59  CRIT <aqofxconnect> provider.c:  783: Error exchanging getStatements-request (-1002)
* 16:05:26  WARN <gnc.import.aqbanking> gnc_ab_gettrans: No AqBanking account found
* 16:05:33  WARN <gnc.import.aqbanking> gnc_ab_gettrans: No AqBanking account found
* 16:06:48  CRIT <aqofxconnect> network.c:  397: Saving response in "/tmp/ofx.log" ...
* 16:06:49  CRIT <aqofxconnect> network.c:  343: Got an error response (500: <BODY><H1>Server Error</H1>Error while processing request by OFX server</BODY>)
* 16:06:49  CRIT <aqofxconnect> provider.c:  783: Error exchanging getStatements-request (-1002)
* 16:08:32  CRIT <gnc.backend.file> commodity_ref_to_dom_tree: assertion `c' failed


ofx.log:
Sending:
-------------------------------------
OFXHEADER:100

DATA:OFXSGML

VERSION:102

SECURITY:NONE

ENCODING:USASCII

CHARSET:1252

COMPRESSION:NONE

OLDFILEUID:NONE

NEWFILEUID:20090405160418.000



<OFX><SIGNONMSGSRQV1><SONRQ><DTCLIENT>20090405160418.000<USERID>xxxxxx

<USERPASS>xxxxxx

<LANGUAGE>ENG<FI><ORG>First Union<FID>4307</FI><APPID>QWIN<APPVER>1700</SONRQ></SIGNONMSGSRQV1><BANKMSGSRQV1><STMTTRNRQ><TRNUID>20090405160418.000<CLTCOOKIE>1<STMTRQ><BANKACCTFROM><BANKID>First Union Sec (PCG)<ACCTID>xxxxxxxx<ACCTTYPE>CHECKING</BANKACCTFROM><INCTRAN><DTEND>20090405160414<INCLUDE>Y</INCTRAN></STMTRQ></STMTTRNRQ></BANKMSGSRQV1></OFX>

Sending:
-------------------------------------
OFXHEADER:100

DATA:OFXSGML

VERSION:102

SECURITY:NONE

ENCODING:USASCII

CHARSET:1252

COMPRESSION:NONE

OLDFILEUID:NONE

NEWFILEUID:20090405160641.000



<OFX><SIGNONMSGSRQV1><SONRQ><DTCLIENT>20090405160641.000<USERID>xxxxxx

<USERPASS>xxxxxx

<LANGUAGE>ENG<FI><ORG>First Union<FID>4307</FI><APPID>QWIN<APPVER>1700</SONRQ></SIGNONMSGSRQV1><BANKMSGSRQV1><STMTTRNRQ><TRNUID>20090405160641.000<CLTCOOKIE>1<STMTRQ><BANKACCTFROM><BANKID>First Union Sec (PCG)<ACCTID>xxxxxxxx<ACCTTYPE>CHECKING</BANKACCTFROM><INCTRAN><DTEND>20090405160639<INCLUDE>Y</INCTRAN></STMTRQ></STMTTRNRQ></BANKMSGSRQV1></OFX>

---

### Post by harphauler on 2009-04-09
Bump

Would there be a better area to ask this question?

Thanx

---

