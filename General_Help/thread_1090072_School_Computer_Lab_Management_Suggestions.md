---
title: "School Computer Lab Management Suggestions"
date: 2009-03-07
forum: General Help
---

### Post by Prospero2006 on 2009-03-07
Hello all,

-My name is Josh Beck, and I teach a seventh/eighth grade Multimedia/Web design class with a magnet technology program in San Antonio. 

-I've been using Ubuntu full time with the kids for two years now.

-I have a very solid/secure image that keeps the students in check for the most part. 

-At our school, we are required to use a proxy that determines where the kids can and can't go.

-The guys who maintain the proxy aren't interested in my input as to what should be blocked or what should be open. So, I have to work within a static ruleset in terms of what the kids can access.

-Recently, my students have discovered this music site:
  [http://jango.com](http://jango.com)
  -Great site. Just not during class.

The Problem I'm Having:

    -I want to code in a rule to /etc/hosts.deny or 
     write an iptables rule that drops all traffic inbound
     or outbound from django. (Something anyway!) 

    -I've identified the ip address, but creating a drop rule
     doesn't seem to be effective. (Browser still brings it up.)

Anyone have any suggestions or ideas on how I might approach the situation. I love to tinker with this stuff, but as of late Django is unstoppable!

Thanks,
Josh Beck

---

### Post by linuxisevolution on 2009-03-07
Well, you could use kiosk possibly... I have never done this before :P

---

### Post by lykwydchykyn on 2009-03-07
It might be a good idea to set up your own proxy, if you have the hardware.  Pretty trivial to do on Ubuntu with squid and Dansguardian.  It might seem like more trouble than an iptables rule, but over time as they discover the next big time wasting site it'll be less trouble for you.

I know there's a "parental controls" gui in the works for Ubuntu, basically a frontend for Dansguardian/Squid.  But I don't know if it will be ready for Jaunty or not. 

When it comes to crafting iptables rules, I'll confess I cheat and use Webmin's firewall interface.  The only problem with blocking IPs that way, though, is that if you have a site with multiple IPs you need to get all the IPs it's using.

---

### Post by DGortze380 on 2009-03-07
keep it simple.

iptables
and
hosts.deny

are very easy to configure

[http://www.linuxsolved.com/linux-forums/general-networking-support-in-linux/how-to-block-certain-ips-and-website-on-iptables-t1438.0.html](http://www.linuxsolved.com/linux-forums/general-networking-support-in-linux/how-to-block-certain-ips-and-website-on-iptables-t1438.0.html)

---

### Post by Prospero2006 on 2009-03-08
TY for the suggestions.
Josh

---

### Post by LegendofTom on 2009-03-08
Hey, that's pretty cool to have your students using good ol' Ubuntu.  Props.

---

