---
title: "lampp - permission denied, how to remove (+ CGI Proxy setup)"
date: 2009-04-30
forum: General Help
---

### Post by raichee on 2009-04-30
Hey, as the title suggests, all files and fodlers in /opt/lampp are 'locked' so to speak.
Now admittedly this was most likely my doing as I probably messed something up whilst setting lampp going.

Now, I've tried sudo chmod which seemed to do nothing (is this recursive?) as well as sudo rm -rf /opt/lampp and both return access denied. My knowledge of Ubuntu and Linux is very poor, but I'm all up for learning. So those 2 means where the best I could think of.

So, simply put, how on earth do I remove lampp?!

For the record I'm trying to set up a [CGI proxy]("http://www.jmarshall.com/tools/cgiproxy") for me to access from college as they have stupidly strict filtering systems. I'd use squid, but unfortunately that will not work at college. If you know that lampp isn't the way to go to get that linked item working, then please let me know how! I chose lampp as I'd used xampp on a Windows box and got on quite well, but only for hosting files and webpages.

Thank you for your time!

---

### Post by raichee on 2009-04-30
For lack of finding a edit button I'll post again. A restart and sudo rm -rf has done the trick at last.

I also managed to get the CGI proxy active via localhost as well as a .ath.cx address with dynamic DNS. However, I really want SSH to be enabled on this thing, and currently it is returning that it isn't secure. Checking synaptic, I have open SSL installed, and it also seems like I have Net::SSLeay installed too. I have never, ever used perl or ssh/l before, so your help would be much appreciated with getting this cgiproxy in /usr/lib/cgi-bin/nph-proxy.cgi (locahost/cgi-bin/nph-proxy.cgi) to work with SSL.
I also want to set up a form of 'log in' so only me or a few trusted friends can actually use it, since it's my bandwidth and computer after all, and I'm pretty darn sure that requires SSH too.

---

