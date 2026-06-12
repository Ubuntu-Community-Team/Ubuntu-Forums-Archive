---
title: "cannot access website after host change"
date: 2008-12-29
forum: General Help
---

### Post by Dawa on 2008-12-29
hello-

a website i visit frequently changed hosts recently - however whenever i try to access the site it still times out.  i have cleared the firefox cache, but it didn't work.  if i boot into windows i can access the site.  So what gives?  My IP address is the same in windows so i haven't been blocked from the site or anything.

how do i get ubuntu to recognize the hosts change?

---

### Post by beynac on 2008-12-29
You could try flushing the DNS cache.

[i]To flush the DNS cache in Linux, restart the nscd daemon:-


    - To restart the nscd daemon, type **/etc/rc.d/init.d/nscd restart** in your terminal
    - Once you run the command your linux DNS cache will flush.[/i] 

I have not done this in Linux, so I can't vouch for this method.

Edit: I have also found this link: [www.ubuntugeek.com/howto-clearflush-dns-cache-in-ubuntu.html]("http://www.ubuntugeek.com/howto-clearflush-dns-cache-in-ubuntu.html")

---

### Post by Dawa on 2008-12-29
this doesn't work.  neither does restarting bind9.

edit: neither does sudo /etc/init.d/networking restart

also i'd like to point out that intrepid doesn't come with nscd by default; installing it just to restart it is pointless.

this is insane.  am i going to have to format and reinstall intrepid just to be able to go to a #&@%ing website?

---

### Post by Dawa on 2008-12-29
okay, i've found out that if i disable Firestarter, i can access the site... however setting up an event policy to allow incoming connections from the site's IP doesn't change anything.  Firestarter has to be off or i can't access the site.

anyone have any advice as to what is going on?  I'd like to be able to continue using my firewall, of course

---

