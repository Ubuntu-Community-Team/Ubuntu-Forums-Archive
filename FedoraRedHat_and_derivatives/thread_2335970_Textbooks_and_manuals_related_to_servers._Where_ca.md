---
title: "Textbooks and manuals related to servers. Where can I find them?"
date: 2016-09-03
forum: Fedora/RedHat and derivatives
---

### Post by issh on 2016-09-03
My friends and I need to set up a server to host a website, set up email, and be able to support a moderate amount of traffic. 

I was thinking of going with Power architecture and Yellowdog Linux 6.2. 

If not Power, then I'm not sure what the best course of action will be. I have read articles discussing PowerMac G5s being used as servers even today.  I'm trying to be thrifty here since we don't have mountains of cash sitting around. 

I know almost nothing about servers and how this is all done, but I'm not a novice to linux. Where can I find textbooks, manuals, and any other information on servers in general?

---

### Post by howefield on 2016-09-03
Thread moved to the "*Fedora/RedHat and derivatives*" forum.

---

### Post by SeijiSensei on 2016-09-03
Can you afford $10/month?  I'd go with a virtual server at [Linode]("https://www.linode.com/linodes").  They don't have Yellowdog, but they have most any other free server flavor of Linux -- Ubuntu, Debian, Fedora, CentOS (my choice), Gentoo, Arch and Slackware.  You pick a distro, spin it up, and you're ready to go. You get a public IP, decent storage and CPU, a managed hosting facility with power, A/C, etc., good support, and excellent tools.  Just a recommendation from a satisfied user.  I also pay a few bucks a month for the [backup service](https://www.linode.com/backups).

In my signature you'll find a link to Linode's collection of support documents.  I suggest you start there.

---

### Post by issh on 2016-09-03
> **SeijiSensei said:**
> Can you afford $10/month?  I'd go with a virtual server at [Linode]("https://www.linode.com/linodes").  They don't have Yellowdog, but they have most any other free server flavor of Linux -- Ubuntu, Debian, Fedora, CentOS (my choice), Gentoo, Arch and Slackware.  You pick a distro, spin it up, and you're ready to go. You get a public IP, decent storage and CPU, a managed hosting facility with power, A/C, etc., good support, and excellent tools.  Just a recommendation from a satisfied user.  I also pay a few bucks a month for the [backup service]("https://www.linode.com/backups").

In my signature you'll find a link to Linode's collection of support documents.  I suggest you start there.

Oh thank you very much. The only thing is that at around 20TB it becomes quite spendy and we will likely need that much storage or more. We will definitely consider this however. It is possible to have a website built and hosted on Linode and it will support a good amount of traffic?

---

### Post by SeijiSensei on 2016-09-04
Sure.  You can contract with a developer and give them limited access to your server so they can upload the site.  If I were you, I'd start at the $10 level and only upgrade if you need to.  As for traffic, I have machines at $10 and $20 per month; they both have a traffic maximum of 3 terabytes a month.  I never come close.

The webserver is running Apache httpd with PHP-based sites and some WordPress blogs, MySQL, PostgreSQL, the Sphinx search daemon, BIND9 to provide name services, and sendmail to accept inbound mail (which is forwarded to another server for processing).  That's on a $10 box.  It hardly breaks a sweat.

Also I was offered free upgrades to both machines.  The $10 box now has 48 GB of storage; the $20 box has 72 GB.  Both have more than the original amount of memory as well.

I manage another $10 box for a client. It serves up a Drupal website along with some mail and DNS services. It doesn't work very hard either.

---

### Post by SeijiSensei on 2016-09-07
> **issh said:**
> Oh thank you very much. The only thing is that at around 20TB it becomes quite spendy and we will likely need that much storage or more. We will definitely consider this however. It is possible to have a website built and hosted on Linode and it will support a good amount of traffic?

Are you really talking about hosting and distributing **20 TB** of content?  The only kinds of sites I can think of needing that much storage are distributing audio and video files.  Assuming your activity is legal, you're going to need a lot more expensive infrastructure than you're imagining.  Something like [Cloudflare]("https://www.cloudflare.com/features-cdn/") might be in your future.

If this content is not legally owned by you, then no professional company like Linode or Cloudflare will want your business.

---

