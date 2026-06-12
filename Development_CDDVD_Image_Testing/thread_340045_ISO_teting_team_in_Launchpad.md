---
title: "ISO teting team in Launchpad"
date: 2007-01-16
forum: Development CD/DVD Image Testing
---

### Post by Henrik on 2007-01-16
On Pochu's suggestion, I set up an [ISO testing team]("https://launchpad.net/%7Eisotesting") in Launchpad. After some discussions with the launchpad team I'll probably also set up some products as well, such as ubuntu-isos, kubuntu-isos, etc. that we can then file reports against.

---

### Post by pochu on 2007-01-16
Hi!

I've just joined the team. Now, let's continue testing and helping others with their test!

Regards
Pochu

---

### Post by DeeZiD on 2007-01-16
I've joined, too and opened [bug 79662]("https://bugs.launchpad.net/ubuntu/+bug/79662")

---

### Post by marcopoloni on 2007-01-17
Hi,
joined as well.
saluti
Marco

---

### Post by UBfusion on 2007-01-18
This is the greatest idea since sliced bread. Great move, I joined.

Currently there many iso bugs spread all around ubuntuforums in an informal way (i.e. not via launchpad). My guess is that this happens because launchpad appears to have a steep learning curve for amateurs like me. Also, help on how to start using the launchpad is not very clear imho and spread in several different posts. For these reasons, people that want to report iso bugs do it in various ubuntuforums and launchpad sections.

I have some ideas that could help get more people involved in ~isotesting:

1. Henrick's announcement of the testing team ([http://www.ubuntuforums.org/showthread.php?t=340045](http://www.ubuntuforums.org/showthread.php?t=340045)) gets sticky

2. The instructions for using launchpad specifically for iso testing are rewritten and stickied **in the same** previous announcement. When newbies have to open 5 different pages to get an idea of how launchpad works, it gets very complicated and they abandon ship.

3. We make a kind of sandbox like e.g. [https://launchpad.net/~isotesting/](https://launchpad.net/~isotesting/)**candidatebugs** where people can post bugs, even in a non-perfect way. Team members try to reproduce the bugs, polish the "amateur" reports and when confirmed, move them to the main isotesting threads.

Bug fixers would then have to read only the main isotesting, and not all the other reports spread here and there, while the test team would focus on collecting and reproducing bugs.

I think that the most important bugs in Feisty isos  now are [https://bugs.launchpad.net/ubuntu/+bug/78810](https://bugs.launchpad.net/ubuntu/+bug/78810) (which contains many bugs) and [https://bugs.launchpad.net/ubuntu/+bug/79662](https://bugs.launchpad.net/ubuntu/+bug/79662). Could some experienced user  "polish" them and move to ~isotesting?

---

### Post by UBfusion on 2007-01-18
> **DeeZiD said:**
> I've joined, too and opened [bug 79662]("https://bugs.launchpad.net/ubuntu/+bug/79662")

Shouldn't that bug appear in [https://bugs.launchpad.net/~isotesting/+assignedbugs](https://bugs.launchpad.net/~isotesting/+assignedbugs) ?

---

### Post by pochu on 2007-01-18
> **UBfusion said:**
> Shouldn't that bug appear in [https://bugs.launchpad.net/~isotesting/+assignedbugs](https://bugs.launchpad.net/~isotesting/+assignedbugs) ?
It hasn't been assigned to the ISO testing team, so it won't appear on the ISO testing team assigned bugs. If it were assigned to us, it would appear in that page.

Regards
Pochu

---

### Post by DeeZiD on 2007-01-18
Sorry, but I don't know how to do that...
Can you explain that to me?

---

### Post by pochu on 2007-01-18
> **DeeZiD said:**
> Sorry, but I don't know how to do that...
Can you explain that to me?
Of course :D

You should go to the [bug page]("https://bugs.launchpad.net/ubuntu/+bug/79662") and then click on the Package/Distro name (now it is Ubuntu)  just below the title, where it says Affects.

Then where it says Assigned to, click on the third button (others) and enter the name of the person/group. Ours is "isotesting".

However, I think you shouldn't assign it to us, because we aren't going to fix it. We are going to debug it, search the cause, search the workaround, the package... but not to fix it. Who is going to fix it is the mantainer of the package affected, or the developer.

So what you can do is to notify the team. To do that, click on the "[Subscribe Someone Else]("https://bugs.launchpad.net/ubuntu/+bug/79662/+addsubscriber")" item on the left menu, and then enter the team name (isotesting). If you do this, the package won't be assigned to us (it shouldn't be, as I've said), but we will be notified if any comment, change, or something is made to the bug report. And the bug will appear [on this page]("https://bugs.launchpad.net/%7Eisotesting/+subscribedbugs")

I hope to have helped to you, and to have been clear enough :D

Regards
Pochu

---

### Post by DeeZiD on 2007-01-18
I did the second thing you've mentioned before.
I've already found a workaround, but it isn't really a workaround because the installer doesn't find any installable kernel (tty4: linux-image-generic not usable on 386) :-k 

But the AMD64CDs work just fine :)


regards Dennis

---

### Post by Henrik on 2007-01-19
Thanks UBfusion. I've forwarded your comments on Launchpad to the LP team. Some better documentation is definitely in the works.

---

