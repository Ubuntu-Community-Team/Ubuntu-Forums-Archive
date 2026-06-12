---
title: "Evolution and Exchange Connector issues"
date: 2005-02-14
forum: Desktop Environments
---

### Post by mastrmind on 2005-02-14
I recently installed Ubuntu on my laptop after a long hiatus from playing with linux, largely because I wanted to use Evolution to access my work email which uses Exchange 2003. Using Warty, Evolution would hang any time I would try to connect to the exchange server, so I decided to upgrade to Hoary. Now when I try to setup the account, I choose Exchange, then enter my domain\user and URL as I use successfully for Outlook Web Access. When I click authentic however, it says:

"Could not authenticate to the Exchange server. Make sure the username and password are correct and try again."

Am I doing something wrong? Could there be something from my previous failures under Warty still causing problems? I assume that any Exchange 2003 server with Outlook Web Access working should work with Evolution without any other setup? And yes, I have tried to get our sysadmin to enable the IMAP ports but he doesn't want to do that.

Thanks for any help.

Ian

---

### Post by lineymo on 2005-02-17
I had (and sort of still having) this same issue.  I recieved that error, then I clicked "BacK" then "Forward" and then clicked "Authenticate"  It was successfull, then I went on to the next page and filled out the Global Catalog field since that was really all there was to do on that screen, but the "Forward" button is disabled.  I can't get any further. :?

---

### Post by landtuna on 2005-03-05
I got past this problem by entering my username as DOMAIN\username.

---

