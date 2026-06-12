---
title: "Doubts about Mono"
date: 2009-06-24
forum: General Help
---

### Post by polax on 2009-06-24
A small intro - I have an ACER m464, the system ships with Vista Business Edition. This was purchased recently, around the same time Ubuntu came out with Jaunty.

I have since installed Jaunty on my system and have booted Vista all of 4 times - primarily because i had problems with my Wireless Router (Hardware Problem), wanting to verify if Vista did a better job at holding the connection than Jaunty. [Edit: It does not - the problem was with the Hardware, not the OS]

I have been since a very very happy Jaunty user. I have been recommending this to my friends and family, and to make a long story short - have been really satisfied with my "desktop experience" with Ubuntu/Gnu-Linux so far. The system is rock-stable, and I don't recollect a single time, when the system has crashed or died on me.

I read an article recently about Mono - and was wondering about the legality of the same. There are conflicting reports on the licensing of the same in the web, and was wondering Ubuntu's official stand on using Mono. Does mono ship as a part of the restricted extras, or is it included in the default install? I use restricted drivers, VLC and a host of other programs which (could possibly) depend on restricted/proprietary code - but with all FUD that MS keeps throwing about, I just want to be clear about this.

Could someone please clarify on this?

---

### Post by directhex on 2009-06-24
> **polax said:**
> A small intro - I have an ACER m464, the system ships with Vista Business Edition. This was purchased recently, around the same time Ubuntu came out with Jaunty.

I have since installed Jaunty on my system and have booted Vista all of 4 times - primarily because i had problems with my Wireless Router (Hardware Problem), wanting to verify if Vista did a better job at holding the connection than Jaunty. [Edit: It does not - the problem was with the Hardware, not the OS]

I have been since a very very happy Jaunty user. I have been recommending this to my friends and family, and to make a long story short - have been really satisfied with my "desktop experience" with Ubuntu/Gnu-Linux so far. The system is rock-stable, and I don't recollect a single time, when the system has crashed or died on me.

I read an article recently about Mono - and was wondering about the legality of the same. There are conflicting reports on the licensing of the same in the web, and was wondering Ubuntu's official stand on using Mono. Does mono ship as a part of the restricted extras, or is it included in the default install? I use restricted drivers, VLC and a host of other programs which (could possibly) depend on restricted/proprietary code - but with all FUD that MS keeps throwing about, I just want to be clear about this.

Could someone please clarify on this?

Official statement from Ubuntu Technical Board:

> === Mono discussion ===

Mono has been the subject of various heated discussions recently. While there is no urgent question to resolve, it seems appropriate for the TB to give it some consideration.

We recently considered the topic of alleged patent violations in some detail. Although the TB meeting in question does not appear to have been written up, logs are available here:

  [http://irclogs.ubuntu.com/2009/03/24/%23ubuntu-meeting.html](http://irclogs.ubuntu.com/2009/03/24/%23ubuntu-meeting.html)

To summarise briefly, we will of course engage with patent holders who contact us with a claim of a patent violation in Ubuntu; the technical board is the correct point of contact for this. Although others are welcome to inform the technical board of allegations of which they have become aware, and any developer with a question or concern about a particular patent should contact the TB who will advise if they are aware of an issue, we will not in general act solely on third-party allegations or rumours. In the case of Mono, Canonical (who would bear most of the liability for any violation) does not currently believe this to be a major risk, as should be evident from the fact that it has been shipped in Ubuntu main since 5.10 and in the default desktop since 6.10.

In general, we will ship the best available free software applications, in the judgement of the relevant development team; the desktop team has responsibility for desktop application selection, as is natural. In a small number of cases, Mono applications have been selected there on their merits. At present, were there to be an issue, Mono would be easy to extricate. Making it more of a core requirement is likely to encounter some performance concerns at present anyway, since the budget for desktop startup is increasingly tight as we work on boot performance.

In short, at the moment, Mono is very well-maintained in Ubuntu and there appears to be no significant cause for concern over its IP situation. We will attempt to clarify in suitable places what developers and/or rights holders should do in the event that they have evidence of a problem.

See: [https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028347.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028347.html)

---

### Post by polax on 2009-06-24
Thanks mate :) - Cheers

---

### Post by jimv on 2009-06-24
> **polax said:**
> 
I read an article recently about Mono - and was wondering about the legality of the same. There are conflicting reports on the licensing of the same in the web, and was wondering Ubuntu's official stand on using Mono. 

Let me make this simple.  Don't believe the FUD. Mono as it is implemented is any Linux app you are likely to use is just fine and legally solid.  The questionable parts are their implementations of WinForms, ASP.NET, and ADO.NET...but these are not used in any Linux apps that come with Ubuntu.

---

### Post by bodhi.zazen on 2009-06-24
> **jimv said:**
> Let me make this simple.  Don't believe the FUD. Mono as it is implemented is any Linux app you are likely to use is just fine and legally solid.  The questionable parts are their implementations of WinForms, ASP.NET, and ADO.NET...but these are not used in any Linux apps that come with Ubuntu.

mono is released under the GPL.

Many of these questions are specifically ansered here ;

[http://mono-project.com/FAQ:_General](http://mono-project.com/FAQ:_General)

Licensing is here : [http://mono-project.com/FAQ:_Licensing](http://mono-project.com/FAQ:_Licensing)

As you can see mono is GPL.

If Microsoft can push any claims on GPL much more then the Mono project is in deep trouble.

Lesson: Go to the source and don't contribute to FUD.

---

