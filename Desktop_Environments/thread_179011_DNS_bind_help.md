---
title: "DNS bind help"
date: 2006-05-18
forum: Desktop Environments
---

### Post by MadCowDzz on 2006-05-18
Please understand, I'm absolutely new to the world of DNS... I'll explain what I'm looking to do, and hopefully someone can let me know if I'm on the right track and what the next steps might be.

In a nutshell, I basically want to set up a global hosts file... Essentially, I've set up host names and stuff in my /etc/hosts which work great locally... Now I've decided I want to access these same hosts from a separate computer (and any computer on my LAN)... for this, I've determined, I need to set up a DNS server.

The hosts I've defined locally are things like: **somename.local** and **somename2.local** The idea of not using real domains and real TLD's is to keep me, or someone on my computer, from being confused. I am interested in doing the same thing and making that accessible anywhere on the LAN.

I am hoping to set up **somename.lan** or **somename2.lan** which would names only accessible from within my network. All of the sample BIND configurations I'm finding are forcing one to set up a proper domain, such as *example.com* 

Is it possible to have my own TLD the way I want?
Is BIND the best choice for me? I've installed it from apt-get and followed [a tutorial](http://www.linode.com/wiki/index.php/Install_BIND9_in_Ubuntu_(Breezy)) for installing it... configuring it feel like a whole new adventure (any links or guidance would be great).

Remember, I'm looking to set this up as 100% private, lan only, dns... any tips?

Thanks!

---

### Post by Blairboy on 2006-05-19
I only know how to set up BIND with an actual domain.  Not sure if you can do it without one to be honest.

---

### Post by MadCowDzz on 2006-05-21
I don't really see why not... but the fact that I can't find any documentation to support my efforts, I guess you can't.

With that being said, I've been having a difficult time setting up BIND in general... anyone have some tips or guides on how to set it up? Again, local install only... and I don't need DNS cache'ing or anything.

All the guides I find don't seem to suit the way the Ubuntu Synaptic install is and I've been struggling to compare the differences.

---

### Post by gdw on 2006-05-27
Hi,

I've been trying to figure out how to do the same thing for my current home network. I managed to setup local DNS some years back at a different location, but now can't remember how I did it - it is possible though.

In doing some research on the topic I've found the following articles that may be of help to you:

[http://www.howtoforge.com/two_in_one_dns_bind9_views](http://www.howtoforge.com/two_in_one_dns_bind9_views)

[http://www.howtoforge.com/traditional_dns_howto](http://www.howtoforge.com/traditional_dns_howto)

Regarding the question of whether Bind is the right tool for the job some posters  over at Debian Administration [[http://www.debian-administration.org/]](http://www.debian-administration.org/]) some posters say it might be overkill for a small network and that it might be worth checking out a lightweight Bind alternative called Dnsmasq [[http://thekelleys.org.uk/dnsmasq/doc.html]](http://thekelleys.org.uk/dnsmasq/doc.html]). I had a look at that app, but have decided to try again with Bind. If you can get your hands on a copy of teh DNS and Bind book [[http://www.oreilly.com/catalog/dns4/]](http://www.oreilly.com/catalog/dns4/]) you'll find it a very helpful resource.

Hope that helps.

- g

---

