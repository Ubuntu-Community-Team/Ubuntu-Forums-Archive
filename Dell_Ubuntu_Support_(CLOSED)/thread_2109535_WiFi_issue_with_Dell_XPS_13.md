---
title: "WiFi issue with Dell XPS 13"
date: 2013-01-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by paddy2k on 2013-01-27
I've been living with terrible WiFi performance my Dell XPS 13 (Ivy Bridge) for the past few months.
In November when I purchased the machine everything was ok, however in the middle of December the first visit to a new domain could take up to a few minutes to complete. So I reinstalled 12.10 (including the Project Sputnik PPA) thinking I had messed up some config somewhere.
 
But the issue persisted.

So last week I did a clean 12.04 install, as it is the only officially supported version of Ubuntu for Project Sputnik. I was delighted that WiFi performance returned to normal, until today.
Once again it's slowed to a crawl.

Elsewhere other users have blamed bad routers etc for their issues, however if I boot into a live Ubuntu USB the browsing performance is perfect, but once I boot from the hard drive, it slows to a crawl.

I've tried modifing the power management as per Wild Man's [instructions]("http://ubuntuforums.org/showthread.php?t=2012228") but that hasn't helped.

Here's a video clip of how bad the connection is, the left pane is a ping to google.com, the right pane is a ping to the same ip address.
[http://youtu.be/Q3fyRgX31l4](http://youtu.be/Q3fyRgX31l4) 
My issue only seems to occur when using a domain name, requests to ip addresses return instantly. I have noticed some errors in my syslog relating to a SIGTERM for dnsmasq, which may have something to do with this.

---

### Post by mikewhatever on 2013-01-27
You should copy/paste the ping results here, along with the syslog errors. Have you tried using a different DNS provider?

---

### Post by paddy2k on 2013-01-28
Thanks for replying. Here's a link to a copy of my syslog after boot.
[http://paste.ubuntu.com/1583859/]("http://paste.ubuntu.com/1583859/")

---

### Post by paddy2k on 2013-01-28
Looks like I caught a break!
Editing /etc/resolv.conf to use Google's Public Nameservers solved the issue.

---

