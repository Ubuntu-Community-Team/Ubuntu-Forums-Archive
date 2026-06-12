---
title: "Thunderbird / Firefox urls not working"
date: 2005-07-09
forum: Desktop Environments
---

### Post by reuben on 2005-07-09
I am using kubuntu; I have setup the components for email & web as firefox/thunderbird in the kde control center. However, when I click on a web link from an email, or a mailto link in a web page, nothing happens. What steps am I missing?

Thanks

---

### Post by mrbit on 2005-07-09
been there done that.

i could point you to the place where i found my answer, but that would be more effort (on both our parts) than just telling the solution: 

TO => Get Thunderbird to open links in Firefox (or any preferred browser): 
       1) Go to [http://aboutconfig.mozdev.org/](http://aboutconfig.mozdev.org/) - to get a utility making it simpler to edit your "user preferences" (in thunderbird, about:config comes with firefox already)
       2) after installation and restarting Thunderbird start up about:config (go to "tools -> about:config")
       3) find the keys for
              network.protocol-handler.app.http   and
              network.protocol-handler.app.https
           (if they don't exist, make them new, as "strings") and set the value for both of them (or at your preference) to your browser binary or symlink or whatever (ie. "/usr/bin/firefox")
        4) restart TB.  test

TO => Get Firefox to open mailto: links with Thunderbird
        well gee.... i thought i had this done, but apparently it's broken and now i want to fix it too.  tried following directions from 
  [http://ubuntuforums.org/archive/index.php/t-18175.html](http://ubuntuforums.org/archive/index.php/t-18175.html)
  [http://www.kryogenix.org/days/2004/12/21/thunderbird](http://www.kryogenix.org/days/2004/12/21/thunderbird)
  [http://www.crazysquirrel.com/debian/firefox-mailto.php](http://www.crazysquirrel.com/debian/firefox-mailto.php)
but they all fail in the same way: if thunderbird is already open (and, duh, it's ALWAYS already open!) then it asks me to choose a profile, that's not acceptable.  who will answer the answerer on this one?

---

### Post by mrbit on 2005-07-09
oh yeah, and here's a good page to test your firefox -> thunderbird implementation:

[http://www.ianr.unl.edu/internet/mailto.html](http://www.ianr.unl.edu/internet/mailto.html)

---

### Post by reuben on 2005-07-10
Cool, that works pretty well. I used the last mailto script from the ubuntuforums link in your reply; it works for simple mailtos, but not for complex ones (e.g. with subjects). Plus, in neither solution does the other app focus for me (altho that's no huge deal.) 

Thanks for your help

---

### Post by chrisod on 2005-07-31
For some reason, the script is not passing the address or subject line information to Thunderbird. Thunderbird opens when a mailto link is pressed, but it's just a blank email.

Any ideas?

---

