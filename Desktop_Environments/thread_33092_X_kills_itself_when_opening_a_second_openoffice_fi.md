---
title: "X kills itself when opening a second openoffice file"
date: 2005-05-09
forum: Desktop Environments
---

### Post by imwithstupid on 2005-05-09
I have a very specific problem:

X kills itself completely (lost connection to :0.0 just like a ctl+alt+bksp) when I open a second open office document.  Note that this only happens about 50% of the time.  (Also, it doesn't matter what method I use to open the doc file-->open or nautilus)

I am running xcompmgr (with shadows only) and transset.  It crashes even if transset is not used.  I have two monitors running off a nvidia 5200fx, using twinview.  

When I started looking into this I suspected xcompmgr.  I will turn it off for now and see if I can eliminate it from the list of possible problems. 

I have looked over the appropriate log files and nothing shows up.

-When the x server kills itself I get a "Fatal server error: Caught signal 11 server aborting"
-.xsession-errors shows nothing interesting at all.  It reports that openoffice is smart enought to use only one instance of itself "Using existing OpenOffice.org" and then it immediately goes to "The application 'gnome-session' has lots its connection to the display :0.0" and then it shows the rest of the progs running losing their connection.

Where else can I look? and what could I possibly run to trace this problem?

---

