---
title: "how to diagnose non-working SSH"
date: 2009-05-09
forum: General Help
---

### Post by MountainX on 2009-05-09
I have 2 computers running Ubuntu 8.10. Both are set up very similar. I can SSH from #1 to #2, but I cannot SSH from #2 to #1. 

Here's the result - it times out after about 2 minutes.
```
ssh user@ip_number2
ssh: connect to host ip_number2 port 22: Connection timed out

```I have checked everything I can think to check:
auth.log
firewall rules (#1 has no firewall and #2 allow all outgoing packets)
router
sshd_conf
denyhosts.conf
ssh myuser@localhost works
and more.

BTW, I can connect to #1 from other computers on my LAN. Computer #2 is outside my LAN. But at least I know #1 can receive SSH connections. 

I cannot seem to find the problem. Any suggestions?

---

### Post by mlissner on 2009-05-09
That sounds like you can't find computer #1. What happens if you ping it?

---

### Post by Ocxic on 2009-05-09
If computer #2 is outside your LAN you'll probably have to setup port forwarding on your router to allow the connection from #2 to #1. 
This may also require Computer #1 to have a static IP address as well.

---

### Post by MountainX on 2009-05-09
> **Ocxic said:**
> If computer #2 is outside your LAN you'll probably have to setup port forwarding on your router to allow the connection from #2 to #1.

I have that set up. I believe it is working because I have some other port forwarding (http and http-alt) that are working correctly. It is easy to set up, and I do not see any place where I could have made a mistake in the setting for SSH.

> **Ocxic said:**
> 
This may also require Computer #1 to have a static IP address as well.
I have a static IP too (DSL).

What diagnostics could I run?

---

### Post by Brandon Williams on 2009-05-09
On computer #2, 'sudo aptitude install tcptraceroute'. Then 'tcptraceroute -n <hostname> 22'. You may want to do this from #1 to #2 first so that you can see how it should look when it's successful. This will tell you (at least) how far the connections are getting from #2 to #1. My guess is that you will see that they are getting to your router and not beyond it, but they could be stopping somewhere else.

You may also want to run tcpdump on #1 while running tcptraceroute so that you can figure out whether it's the inbound or the outbound packets that are getting lost.

---

### Post by MountainX on 2009-05-09
> **Brandon Williams said:**
> On computer #2, 'sudo aptitude install tcptraceroute'. Then 'tcptraceroute -n <hostname> 22'. You may want to do this from #1 to #2 first so that you can see how it should look when it's successful. This will tell you (at least) how far the connections are getting from #2 to #1. My guess is that you will see that they are getting to your router and not beyond it, but they could be stopping somewhere else.

You may also want to run tcpdump on #1 while running tcptraceroute so that you can figure out whether it's the inbound or the outbound packets that are getting lost.

Thank you. I did try the regular traceroute (& without port number) from #2 to #1 and it appeared to succeed (I'm not sure how to interpret the last few lines of its output). Anyway, I will try it with 'tcptraceroute -n <hostname> 22' and report back...

---

