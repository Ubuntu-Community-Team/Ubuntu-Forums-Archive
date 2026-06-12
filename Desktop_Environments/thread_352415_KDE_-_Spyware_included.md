---
title: "KDE - Spyware included?"
date: 2007-02-03
forum: Desktop Environments
---

### Post by dico on 2007-02-03
Hello,

I'm running Kubuntu Dapper 6.06 with KDE 3.5.5 from Kubuntu.org. I use mainly Fluxbox.

If Fluxbox starts, I noticed a connection to "tango.rb.xcalibre.co.uk" with conky. No Programms or Services, which needed an I-netconnection are active. Only Amarok starts at startup.

After i added `.xcalibre.co.uk' to my hosts.deny i got an error message called "can't talk to klauncher" if i started konqueror or amarok. The Sidebar in both apps doesn't work anymore.


Can someone confirm this?
Does "tango.rb.xcalibre.co.uk" belong to kubuntu.org?
How can i use the KDE-apps without spying?

Thanks for helping.


Sorry for my bad english. I speak usually german. ;)

---

### Post by yuanfangcan on 2007-02-03
I also want to know this.             I don't use any anti-virus software under my ubuntu. Do we need anti-virus software under LINUX? 

Thanks

---

### Post by mangz74 on 2007-02-04
dico

I have been using KDE for sometime now and I have never heard of this issue.  I wanted to recreate the problem but the only thing missing is I do not use fluxbox.  Could it be a fluxbox problem?  That page doesn't look like its from KDE.

yuanfangcan

:confused: you don't really need to use antivirus...since linux has only about 40 viruses compared to window's 60,000.  And by the time the virus infects your computer...:-k a linux developer would have found a fix already.  But if you really want to have antivirus for your Linux/Ubuntu box..you can download clamav or klamav (for kde) from apt. :)

---

### Post by joakim2 on 2007-02-04
> **dico said:**
> Hello,

I'm running Kubuntu Dapper 6.06 with KDE 3.5.5 from Kubuntu.org. I use mainly Fluxbox.

If Fluxbox starts, I noticed a connection to "tango.rb.xcalibre.co.uk" with conky. No Programms or Services, which needed an I-netconnection are active. Only Amarok starts at startup.

After i added `.xcalibre.co.uk' to my hosts.deny i got an error message called "can't talk to klauncher" if i started konqueror or amarok. The Sidebar in both apps doesn't work anymore.


Can someone confirm this?
Does "tango.rb.xcalibre.co.uk" belong to kubuntu.org?
How can i use the KDE-apps without spying?

Thanks for helping.


Sorry for my bad english. I speak usually german. ;)

I don't run Kubuntu so I can't say exactly what's going on, but a qualified guess would be that you have some of the functions of Amarok (or other programs) which need to communicate over the network to function (lyrics retrieval, last.fm or whatever it may be).

---

### Post by kerry_s on 2007-02-04
Yeah, i say it's probably amarok looking up radio stations. Try not having it start and see if you still get that connection. Check the amarok settings and see if you see anything that is setup to call out.

---

### Post by dico on 2007-02-05
Thanks for your opinions, guys.

I tested it with KDE to -> same problem.
I made a systemscan yesterday with clamav. -> no real viruses found. Only exceeded file size  limit in archives, but no kde related files.
LastFM, Lyrics, Podcast and Wikipedia and so on are connecting to other hosts. 

My main question is: Why can't i use the sidebar in konqueror and amarok while i blocked this site?

---

