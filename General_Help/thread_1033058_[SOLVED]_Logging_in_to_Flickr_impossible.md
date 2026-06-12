---
title: "[SOLVED] Logging in to Flickr impossible"
date: 2009-01-07
forum: General Help
---

### Post by Camilia on 2009-01-07
I click to sign in and get this message:
Secure Connection Failed
An error occurred during a connection to login.yahoo.com.
Can't connect securely because the SSL protocol has been disabled.
(Error code: ssl_error_ssl_disabled)

I recently did this:
Type "about:config

1.
network.http.pipelining 
network.http.pipelining.maxrequests 
network.http.proxy.pipelining 

2.
Alter the entries as follows: 
Set "network.http.pipelining" to "true" 
Set "network.http.proxy.pipelining" to "true" 
Set "network.http.pipelining.maxrequests" to some number like 30. 

3.
Lastly right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it receives. 

Since then when I click on a link in my mail I get this message:
Could not initialize the application's security component. The mostly cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not ful or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.

Also in internet see I have firestarter. Possible an upgrade. I thought maybe it was the cause. Tried to activate but failed

Surfing the web got slower and slower, thus I did a complete restore.  Son-in-law says it is better to fix things but I was uncertain if I had clicked something in error trying to mark true. Then I wasn't able to get on the web at all. So I did a restore with the PC factory CD.

---

