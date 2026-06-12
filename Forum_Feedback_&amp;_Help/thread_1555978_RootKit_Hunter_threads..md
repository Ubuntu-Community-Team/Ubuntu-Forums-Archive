---
title: "RootKit Hunter threads."
date: 2010-08-18
forum: Forum Feedback &amp; Help
---

### Post by uRock on 2010-08-18
They keep popping up with false positives. Is it possible to come up with a list of known false positives and place them in a sticky thread in the Security sub-forum to aid those who are new to the rootkit programs? 

I would gladly run the RKhunter against a fresh install just to get the list to start the thread, but I don't want to do it, then have it sink off of the front page and disappear. 

Thanx,
uRock

---

### Post by cariboo on 2010-08-18
It's a good idea, but if the members don't even search for similar threads, I don't think they'll look for a sticky.

---

### Post by bodhi.zazen on 2010-08-19
I disagree, but I am not opposed to any effort to improve the situation.

As I have posted on many of these threads, IMO, the OP needs to be directed to RTFM.

I know it sounds harsh, but, IMO :

1. root kits are complex and to identify and to remove one takes skill.

2. The whole point, IMO, or using a tool such as rkhuner, is for the user to use the information provided in the "warnings" to learn something about how his or her system works.

3. The vast majority of these warnings are well documented with even the most superficial of google searches and the README and FAQ are well written

[http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/README](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/README)

[http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/FAQ](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/FAQ)

4. rkhunter does not give a lot of false positives, it gives "warnings". It is rare that it will indicate a rootkit.

5. Most important, we have a very limited understanding of the environment rkhunter is run. Is this a fresh install ? Is the system "known good" or is there actually a rootkit suspected ? Desktop or server ? etc. IMO these warnings really need to be understood and investigated and we do these people a greater disservice if we do not teach them to learn from these tools.

So, again IMO, if people are unwilling to put in the time, they should not user the tool. We should guide them to the documentation and support the learning process.

If they have questions after reading the documentation we can help.

---

### Post by uRock on 2010-08-19
Bodhi.zazen, very good points that I didn't think of. I was hoping to find a way to help those guys, but it truly looks as if the only thing that could be helpful is maybe a few links pointing in the right direction, but then as Cariboo points out they probably wouldn't bother with looking at the sticky.

Thanks,
uRock

---

### Post by bodhi.zazen on 2010-08-19
> **uRock said:**
> Bodhi.zazen, very good points that I didn't think of. I was hoping to find a way to help those guys, but it truly looks as if the only thing that could be helpful is maybe a few links pointing in the right direction, but then as Cariboo points out they probably wouldn't bother with looking at the sticky.

Thanks,
uRock

=)

Well, that is a potential "black hat" technique you know. Trigger and alarm so many times with "false alerts" that it annoys the sys admin and is disabled.

It is critical to start with a known good and know how these tools work. The vast majority of these tools are designed to give "alerts" or "warnings" and most of the time the err on the side of caution (ie an alert) rather then a false negative (not generating an alert to a potential problem).

At the end of the analysis to use security tools on Linux you need to be willing to read and investigate and one needs to understand a system in some depth to determine how to respond to such alerts.

Any suggestions you have to encourage people to read and learn these tools would be appreciated.

---

### Post by uRock on 2010-08-19
> **bodhi.zazen said:**
> =)

Well, that is a potential "black hat" technique you know. Trigger and alarm so many times with "false alerts" that it annoys the sys admin and is disabled.

It is critical to start with a known good and know how these tools work. The vast majority of these tools are designed to give "alerts" or "warnings" and most of the time the err on the side of caution (ie an alert) rather then a false negative (not generating an alert to a potential problem).

At the end of the analysis to use security tools on Linux you need to be willing to read and investigate and one needs to understand a system in some depth to determine how to respond to such alerts.

Any suggestions you have to encourage people to read and learn these tools would be appreciated.
Understandable. I'll try to direct them to the links you mentioned above and let them go from there.

---

### Post by bodhi.zazen on 2010-08-20
After considering this post, I re-stuck my apparmor, HIDS, and NIDS threads in the security section. Feel free to reference them at will as well as PM me suggestions for improvements.

---

### Post by uRock on 2010-08-20
> **bodhi.zazen said:**
> After considering this post, I re-stuck my apparmor, HIDS, and NIDS threads in the security section. Feel free to reference them at will as well as PM me suggestions for improvements.
Awesome. If I think of anything, I'll let you know.

---

