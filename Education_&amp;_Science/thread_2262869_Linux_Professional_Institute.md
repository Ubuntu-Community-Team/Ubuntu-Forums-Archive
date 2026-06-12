---
title: "Linux Professional Institute"
date: 2015-01-27
forum: Education &amp; Science
---

### Post by ruby4 on 2015-01-27
Hello Ubuntu Community,

Have any of you tried out lpi.org for Linux certificates? I am considering doing a self study using books that support lpi.org and was wondering if anybody has opinions on this institution.

Thanks
Ruby

---

### Post by TheFu on 2015-01-28
> **ruby4 said:**
> Hello Ubuntu Community,

Have any of you tried out lpi.org for Linux certificates? I am considering doing a self study using books that support lpi.org and was wondering if anybody has opinions on this institution.

Thanks
Ruby

It depends on where you are in the world which certs are preferred. In the USA, Redhat certificates are preferred and that shows in the salary (15% higher). Most commercial organizations who run commercial Linux will run RHEL here. However, the US government only requires "a certificate" and the LPI one is the cheapest to get into the door.

When I've asked about OSes in other countries, RHEL hasn't been the main corporate OS deployed, so I would expect that the Redhat certs aren't as important.

The point of certificates is to show to HR that you have a baseline set of skills. There are other ways to get around that, especially if you are a little older where certs just can't touch the deep knowledge gained running UNIX systems daily for 20 yrs.  A few years ago, I looked at some LPI training materials. Most were 8+yrs old and in one book, they were teaching things I've never seen used in the real world across thousands of servers. This was old-school network/host settings that were replaced in the early '90s by other solutions and have been replaced again in the last few years. After that one example, I didn't continue, but I don't need a cert to get a job. Experience counts more.

The Linux Foundation has made their non-distro specific course available online for free at edx.com. You can get a cert from them for a nominal cost (for certain values of nominal) upon successful completion of the course.  They estimate the course will require 40-60 hours of work.

---

### Post by ruby4 on 2015-01-28
Thanks for the insight. I have been diving heavily in this book, it's the essentials, but I am learning a lot more than I have in my years of toying around with OSs.

---

### Post by TheFu on 2015-01-28
> **ruby4 said:**
> Thanks for the insight. I have been diving heavily in this book, it's the essentials, but I am learning a lot more than I have in my years of toying around with OSs.

Everyone has gaps in their knowledge. 
I find the key is to know what is possible and be able to find how to complete/enable it. This is good for a sysadmin who is risk adverse. 

It is bad for developer of new systems, since doing things that have already been done before doesn't lead to new gains for the community.

Nothing can replace experience and a good mentor. 

Any well-written book will lead the reader through the knowledge, building as the book progresses. That is where google results fail. We never know what prior skills are needed or what skill level the author of an online article really holds. With a book that is published, I like to think the publisher did their homework and got someone with enough expertise to limit any mistake, plus they are reviewed by others.

Even reputable websites, like IBM.com with their Linux tutorials can have huge mistakes.  I was reading an article there just last week on how to do something and I knew the writer was suggesting using **sudo** when it just isn't needed and actually is a huge security problem. The author had a gap in his knowledge - like we all do - but rather than solve it, "use sudo" was the answer.  Running most programs does NOT require sudo. If it does, something needs to be fixed with your permissions.  Usually it is just a group needs to be added to your account. Never run any GUI program with sudo/root. Bad things happen - not immediately.

---

