---
title: "AppArmor blocks Zotero"
date: 2010-08-13
forum: Education &amp; Science
---

### Post by michopop on 2010-08-13
After upgrading to Ubuntu 10.04 I had a problem using Zotero (a full discription of the problem - on the zotero forum: [http://forums.zotero.org/discussion/11429/1/zotero-in-ubuntu-104-lucid-lynx/](http://forums.zotero.org/discussion/11429/1/zotero-in-ubuntu-104-lucid-lynx/)). After few unseuccessfull tries I was given a solution on the zotero forum - to switch off AppArmor (the last replys on the quoted topic), which worked. 

My questions are: Is it safe to use Ubuntu with AppArmor switched off? If not - what is the way to have the AppArmor switched on and let Zotero function normaly?

---

### Post by gunksta on 2010-08-16
Sorry for the slow reply. Too many pots, not enough fires. (Please send matches.) While I am more than willing to throw out some thoughts on this, this question is probably better suited to one of the more general areas of the forums, such as the [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331") forum. Most of the topics on this sub-forum are oriented to helping people learn about new tools (such as Zotero) or working on random/various research related questions. Especially numerics and statistics. This is really more of a configuration question and you would undoubtedly get more comments on a forum more geared to helping people make their computers work.

Anywho.

AppArmor, SELinux, etc. are all frameworks to increase the security of Linux systems. However, even without these systems, Linux is reasonably secure. Of course there are ways to subvert your own security such as failing to update your system or using weak passwords which can lead to a compromised system, even if you are running AppArmor or some other additional security system.

Put simply - AppArmor does increase the security of a system, but it's not the end of the world if you choose to turn it off or disable it. 

But, this seems inadequate to me because I can't figure out why AppArmor is affecting Zotero in the first place. I may have to install it on a machine and see if I can replicate this problem locally. AppArmor does not affect everything. It only affects software with AppArmor profiles. These profiles tend to focus on web-services, server stuff, etc. I can see that on my system, there IS a firefox profile, but it is disabled by default. Thus, AppArmor should not affect firefox.

Which leads me to ask - What do you see in /etc/apparmor.d/ ? And, what do you see in /etc/apparmor.d/disable/ ?

Rather than disable AppArmor completely, it would be better if we can identify the offending AppArmor profile and either improve it so that it does not interfere with Zotero (and file a bug report with Launchpad) or simply disable the offending profile and leave the rest of AppArmor run in peace (while also filing a bug report against the offending profile).

Thus, while I am glad you have found a temporary work-around for your problem, I think we should dig a little deeper and fix the root of the problem.

---

### Post by michopop on 2010-11-09
Gunksta, I would like first to excuse for dissapearing from the topic after puting the question. After few days without an answer I gave up for some time, because I had a lot to write and I simply continued to make the references manually. Now I came back to the referencing issue, I checked the topic and I saw you answer. Thank you a lot for answering me so thoroughly and systematically. I would be very glad if you are still willing to help me further with this issue. I understand that it's not the end of the world if I disable AppArmor, but the second solution seems to me as a better one. Now, your questions:

Under /etc/apparmor.d/ i see:

[PHP]abstractions    gdm-guest-session  usr.bin.firefox    usr.sbin.mysqld-akonadi
cache           sbin.dhclient3     usr.bin.freshclam  usr.sbin.tcpdump
disable         tunables           usr.sbin.cupsd
force-complain  usr.bin.evince     usr.sbin.mysqld[/PHP]The /etc/apparmor.d/disable/ folder is empty.

---

### Post by michopop on 2010-11-09
In the meantime I found a new solution on the zotero website: [http://www.zotero.org/support/word_processor_plugin_troubleshooting#apparmor](http://www.zotero.org/support/word_processor_plugin_troubleshooting#apparmor), with a reference to this discussion. I tried it and it works. Is the disabling the AppArmor Firefox profile what you ment in your answer: 

> Rather than disable AppArmor completely, it would be better if we can  identify the offending AppArmor profile and either improve it so that it  does not interfere with Zotero (and file a bug report with Launchpad)  or simply disable the offending profile and leave the rest of AppArmor  run in peace (while also filing a bug report against the offending  profile).

There are few new comments on my thread on the Zotero Forum: [http://forums.zotero.org/discussion/11429/2/zotero-in-ubuntu-104-lucid-lynx/](http://forums.zotero.org/discussion/11429/2/zotero-in-ubuntu-104-lucid-lynx/). The last answer lead me to the solution from the previous link: 

> michopop: The troubleshooting page has had instructions on [disabling AppArmor for just Firefox]("http://www.zotero.org/support/word_processor_plugin_troubleshooting#apparmor") for a while.

Even  more fine-grained changes might be possible&#8212;adding to AppArmor's  Firefox profile exactly what's required to let Zotero work&#8212;but you'd  have to figure out how to do that. 			

What do you think about the possibility of making the mentioned "fine-grained changes"?

---

### Post by gunksta on 2010-11-11
> **michopop said:**
> /etc/apparmor.d/disable/ folder is empty.

That's weird. AFAIK, my AppArmor profiles are exactly as provided by Canonical. In /etc/apparmor.d/disable/ I have links to the firefox profile listed in /etc/apparmor.d/.

Weird.

Turn off FF and then try this.

```
sudo ln /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/usr.bin.firefox
```
This should create a hard link, so that AppArmor ignores the FireFox profile. Try that and see if Zotero runs.

---

### Post by gunksta on 2010-11-11
> **michopop said:**
> What do you think about the possibility of making the mentioned "fine-grained changes"?

We can try. For the record, I have never written or edited an AppArmor profile. If my ideas/suggestions kill Firefox and or eat your children, I claim no responsibility.

:guitar:

---

### Post by michopop on 2010-11-12
I already tried this (I think it has the same function - to disable the firefox profile) and it works: 

[PHP]sudo aa-complain /etc/apparmor.d/usr.bin.firefox[/PHP]

Still, I think I am not ready at this moment for the adventure of making more radical changes, especially if my firefox and family are endangered with it... I am not a programer (I study Philosophy) and sometimes my ubuntu adventures last even few days (when I screw something up and then try to fix it)... I am glad that it finaly works this way! 

Thank you a lot for the help!

---

### Post by heinorr on 2011-01-29
Hey

I had the same problem. I fiddled with the firefox apparmor profile and I could get it to save the downloads in a non-standard directory (in fact, on a NTFS partition). But apparently these right aren't inherited by subprocesses like zotero, and I couldn't figure out how this might work. So I added firefox to the disable directory using gunksta's suggestion. If you want to see the effect immediately, then you should also reload apparmor using
```
sudo /etc/init.d/apparmor reload
```. Then everything works as it used to before upgrading to Lucid/Maverick

---

