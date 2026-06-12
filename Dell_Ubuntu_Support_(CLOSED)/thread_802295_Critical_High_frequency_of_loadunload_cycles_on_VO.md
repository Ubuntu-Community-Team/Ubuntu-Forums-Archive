---
title: "Critical: High frequency of load/unload cycles on VOSTRO 1400 Bug"
date: 2008-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ukripper on 2008-05-21
Is hard-disk ticking bug(load/unload cycle) still in hardy ( Vostro 1400)? Please can anyone confirm that for me? I had it on gutsy and I had to use hdparm workaround to fix that in 7.10.

Bug:[https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

This is very critical bug and I really hope that is fixed in Hardy!


From the above link: an interesting post:




"ethanay wrote on 2008-05-12: (permalink)

[B][I]
for people without heat problems, the ugly fixes for /etc/pm/*.d/ or /etc/acpi/*.d/ will work just fine. However, for people who have heat problems or require shock protection, the solution is much more complicated. furthermore, a solution for everyone is the most complicated, because it has to take into account both of the previous.

like someone else has pointed out, an ugly fix such as hdparm -B 254 is NOT a viable fix for Canonical to release for everyone because some people are dealing with excessive heat problems. This means that they have to work much harder to develop a more sophisticated solution to the problem that will be OK for everyone: appropriate apm settings for both unoptimized hdd i/o and also settings to optimize hdd i/o to allow for aggressive apm. given the complex software environment that this situation exists in, that takes time to develop and test.

however, i agree with others pointing out that it seems communication from Canonical to the general user population on this issue has been extremely lacking. that seems to me to be the bigger issue that this bug has exposed. either this is a fluke, or Canonical needs to use a more effective communications model in order to get messages out to the general user base."[/I][/B]

---

### Post by niteshifter on 2008-05-21
I suppose that horse is not quite dead yet, so let's beat on it some more. After all this is what, going on two years now? :)

It's not a Ubuntu "bug". That link you gave clearly shows it to affect Fedora, Mandriva, and SUSE. Further reading of the link discloses some workarounds you can experiment with.

Yes, we users should not have to do this. But it is what it is: A lack of information - not from Canonical, nor Mandriva, nor Novell - from the hard drive and BIOS manufacturers. Quite a few of which have agreements with Microsoft. Thus, the problem is not only technical, there's a legal aspect to it as well.

Try some of the workarounds given in that link. Have some patience, someday it will be resolved - but remember lawyers bill by the hour ;)

---

### Post by ukripper on 2008-05-21
> **niteshifter said:**
> I suppose that horse is not quite dead yet, so let's beat on it some more. After all this is what, going on two years now? :)

It's not a Ubuntu "bug". That link you gave clearly shows it to affect Fedora, Mandriva, and SUSE. Further reading of the link discloses some workarounds you can experiment with.

Yes, we users should not have to do this. But it is what it is: A lack of information - not from Canonical, nor Mandriva, nor Novell - from the hard drive and BIOS manufacturers. Quite a few of which have agreements with Microsoft. Thus, the problem is not only technical, there's a legal aspect to it as well.

Try some of the workarounds given in that link. Have some patience, someday it will be resolved - but remember lawyers bill by the hour ;)

I never said in my post that workarounds provided there are not working for me. Being a power user for me it ain't a problem. 

I am not bashing canonical or any other distros. This post is quiet recent, so thought might share.

However, all I want to know is if anyone has tried Hardy on VOSTRO 1400 and having this issue still going on that, please confirm. 

I know there are workarounds and I have applied them on day one I got my laptop, that is not an issue. I have followed this bug very closely and I do know if there is legal implications to it or not.

---

### Post by niteshifter on 2008-05-21
Ok .... at that link, where this is displayed (and highlighted):

acpi-support (Ubuntu) - in the Affects column.
Triaged - in the Status column.
Look down five lines: **Nominated for Hardy**. A bit of searching for "Hardy" on that page and ...

No question - it's in Hardy. It has workarounds (triaged). The Debian "Fix" is the hdparm -B 255 workaround.

More searching of that page ... yes it affects Vostros as well. Including the 1400 (a bit more than halfway down).

Now note at the top of the page, that message about 5 duplicates. Hence my "dead horse" comment. By bringing it up - yet again - on this forum we're upping the noise and depressing the signal. Giving your post a subject line beginning with "Critical" catches eyeballs and is likely to promote yet another launchpad report and re-kindle a discussion that has been done to death already. I get it - you're not happy. I'm not happy about this either, there's a whole heap 'o people not happy - but it is being worked on.

So let's let the people working on it do so without further distraction ...

---

### Post by ukripper on 2008-05-22
Sorry mate this is critical bug and will remain critical till it is fixed. 

Normal users won't use these complicated workarounds at all, which is already causing problems for some laptop users whom I support a sort of beware feeling. Therefore, i am forced to develop applications for windows as well which I otherwise won't need to if all my users use linux.

This bug is on my priority list to get resolved so I can convince my remaining users to move to linux.

I have full faith in ubuntu developers and other distros developers. Together we shall find the common fix soon.

---

### Post by usprey on 2010-10-22
Hi, just wanted to comment how surprised i was to see this bug is so old. I guess it will be a long night of reading the aforementioned [bug report]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/59695")... :(

---

