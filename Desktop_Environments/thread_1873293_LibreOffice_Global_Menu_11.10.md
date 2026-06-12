---
title: "LibreOffice Global Menu 11.10"
date: 2011-11-01
forum: Desktop Environments
---

### Post by svenole on 2011-11-01
When opening a LibreOffice spreadsheet stored as read only (typically this happens when opening a spreadsheet directly from an email attachment) running ubuntu 11.10, the integration between LibreOffice and Global Menu fails. The libre office  choices are not present in global menu and choices like save as (to actually store the spreadsheet) is not availble. Now, if you happen to full screen the spreadsheet window, there is no way to get it down to single window size again and you are kind of lost (there are ways around this, but anyway). I would assume that this is a bug? Why should the global menu choices not appear when the calc document is read only? This works with writer and presentations.

---

### Post by vasa1 on 2011-11-01
I got rid of it very quickly. It needs a lot of work.

---

### Post by svenole on 2011-11-02
So you did a lot of work very quickly..;-) Do you know if this has been filed as bug with LibreOffice (calc)?

---

### Post by typhoon_tip on 2011-11-02
There is a bug opened in Launchpad already but... the "read only" !!!!!! You just identified what seemed to be a random issue ! Is really related to the read-only state ! This is why is not happening on any file that you open from Thunderbird, for example. You need to add this feedback to the BUG, it is extremely important. I cannot open Launchpad at the moment, as soon as I can I will post you the link for the bug.

---

### Post by typhoon_tip on 2011-11-02
S*** connection not working now, I managed to get back the bug number: #842566

Please post your findings there if you have an account.

---

### Post by svenole on 2011-11-02
Now, I've done some more checking since you mentioned Thunderbird. This fault is NOT present when opening a calc document attached in an email when using thunderbird as email client.  I use webmail a lot (Exchange 2010 OWA) and this works also FINE opening a calc attachment using the Chrome browser accessing my exchange account. 

The problem does occur when opening a calc attachment in an email when using either Evolution (MAPI) or Firefox (OWA) to access my Exchange 2010 account. It is a calc only problem. 

You can probably see this problem making a calc file read only and then open it via file -> open in Firefox

---

