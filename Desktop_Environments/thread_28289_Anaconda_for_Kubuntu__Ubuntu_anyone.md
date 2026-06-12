---
title: "Anaconda for Kubuntu / Ubuntu anyone?"
date: 2005-04-19
forum: Desktop Environments
---

### Post by vvu on 2005-04-19
Thi story is awhile back but it did answer my question...can we have Anaconda brought over to Kubuntu/Ubuntu - [http://linux.slashdot.org/article.pl?sid=04/11/23/027220&tid=90&tid=106](http://linux.slashdot.org/article.pl?sid=04/11/23/027220&tid=90&tid=106)  - the answer is obviuosly YES!  

Before the die hard CLI people start puncing about the need...there is NO need but it DOES spread Linux / Ubuntu even further into the mainstream with simplification - PERIOD.  The goal is to spread.

---

### Post by JuanC on 2005-04-19
In Kubuntu there is no reason to include Anaconda because it uses GTK , and Kubuntu uses QT , there is no space to include both libraries into a CD.

The solution would be to make an installer using QT  :D

---

### Post by az on 2005-04-19
[QUOTE=vvu]Thi story is awhile back but it did answer my question...can we have Anaconda brought over to Kubuntu/Ubuntu - [http://linux.slashdot.org/article.pl?sid=04/11/23/027220&tid=90&tid=106](http://linux.slashdot.org/article.pl?sid=04/11/23/027220&tid=90&tid=106)  - the answer is obviuosly YES!  

Before the die hard CLI people start puncing about the need...there is NO need but it DOES spread Linux / Ubuntu even further into the mainstream with simplification - PERIOD.  The goal is to spread.[/QUOTE]

Actually ,anaconda for debian (Progeny) is beta.  

[http://componentizedlinux.org/anaconda/documentation/about](http://componentizedlinux.org/anaconda/documentation/about)

It installs Componentized linux, and not really debian.

Anaconda is much slower than the debian installer.  The debian installer is quite impressive.  It includes hooks so that you can potentially tie in a graphical frontend.  This is the plan for upcoming versions of Ubuntu.

This is another way that Ubuntu will improve debian.

What happens when you try to use an anaconda installer on a system that does not have enough ram?

---

### Post by Bob D. on 2005-04-19
Jeff Waugh from Canonical explaining why Ubuntu will not use Anaconda. From the ubuntu-devel maillist. You can read through the entire thread here: [http://lists.ubuntu.com/archives/ubuntu-devel/2004-September/000253.html]("http://lists.ubuntu.com/archives/ubuntu-devel/2004-September/000253.html")

=========================================

On Tue, 2004-09-28 at 22:36 -0500, John Hornbeck wrote:
>[i] Is there no way to hack the Progeny Anaconda installer to work with
[/i]>[i] Ubuntu?  Seems like not much would really need to be changed. Just a
[/i]>[i] thought.
[/i]
Anaconda is an old codebase put through the wringer to support a
different operating system. Lots of cruft and workarounds. On the other
hand, our modified d-i is surprisingly simple (once you get the zen of
it), and we have a primary developer on the team.

Also, we're down to less than ten questions. Anaconda for Progeny sits
around twenty. Removing them would be challenging, particularly when you
consider the codebase as described above. :)

So it seems the quickest way to a maintainable graphical installer (and
worthwhile contributions to Debian) is not Anaconda. :)

- Jeff

---

