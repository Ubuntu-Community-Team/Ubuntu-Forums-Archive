---
title: "Ubuntu software center vs Synaptic"
date: 2012-02-08
forum: Desktop Environments
---

### Post by Azyx on 2012-02-08
I wonder what the diffence are between Software center and Synaptic? I have notice that software center are not able to find 'gnome-session-fallback' or indicator-multiload in the software central.

---

### Post by sikander3786 on 2012-02-08
There shouldn't be a problem like Synaptic can find a package whereas Software Center can't. The software comes from repositories and if the package specific repositories are enabled, it will be listed in Synaptic, Software Center, apt-get, aptitude, whichever package manager you choose.

A brief comparison here:

[http://www.tuxgarage.com/2011/09/installing-synaptic-in-ubuntu-oneiric.html](http://www.tuxgarage.com/2011/09/installing-synaptic-in-ubuntu-oneiric.html)

As far as my opinion is concerned, Synaptic is superior than USC, at least as of now.

---

### Post by Frogs Hair on 2012-02-08
I like synaptic because of the view options on the left pane , but I use both . I have seen multiload for 11.10 as a PPA but didn't it was available in synaptic .

---

### Post by Azyx on 2012-02-08
> **Frogs Hair said:**
> I like synaptic because of the view options on the left pane , but I use both . I have seen multiload for 11.10 as a PPA but didn't it was available in synaptic .

I searched for 'fallback' and 'multiload', but did not get any hit in software center, but with synaptic I get hits. I think. I can't check again because I have both installed now. I have not add any PPA on my new system (yet).

---

### Post by grahammechanical on 2012-02-08
I am using 12.04 and Ubuntu Software Centre has both of those packages in it.

I can find Gnome-session-fallback by searching for that term or by searching for Gnome-session. That brings up Gnome Session Manager which is already installed and from there I get Add-on options of Gnome shell and Gnome Session Manager-Gnome Fallback session.

By searching for indicator I got to something called System Load Indicator which is at version indicator-multiload 0.2-0ubuntu1.

I do not have a ppa in Software sources for either of these two packages.

Regards.

---

### Post by bluexrider on 2012-02-08
I prefer synaptic. It has more information available.

---

### Post by cortman on 2012-02-08
Synaptic. It shows dependent packages clearly and allows you to create download scripts for offline installation. I've found it to be more reliable as well.

---

### Post by Azyx on 2012-03-01
grahammechanical.  You may have right...that it work...

But it seems harder to find things in Software center? How do you see if the packade are supportet by Ubuntu i Software center? In synaptic you have the ubuntu-symbol for that, I think, or do  software center just have Ubuntu supported software?

PS. Try to find Xubuntu-desktop or Lubuntu-desktop in SC.

On other hand if you not know what you need it seems to be better information about the application in SC.

---

### Post by markbl on 2012-03-01
> **bluexrider said:**
> I prefer synaptic. It has more information available.
Software center is for noobs only. Synaptic is for everybody else.

---

### Post by bfengineer on 2012-03-07
Hi all,

I have a question in this regard. Please bear with me. I'm very much new to Linux. In my Ubuntu 6.1 (Which I actually like more than the new one) the synaptic package manager has stopped working. Is there any way that I can point it to a server that still supports it? I've tried selecting different software sources. Sorry if this is posted in the wrong thread. Any help will be appreciated. Regards.

---

### Post by Azyx on 2012-03-07
> **bfengineer said:**
> Hi all,

I have a question in this regard. Please bear with me. I'm very much new to Linux. In my Ubuntu 6.1 (Which I actually like more than the new one) the synaptic package manager has stopped working. Is there any way that I can point it to a server that still supports it? I've tried selecting different software sources. Sorry if this is posted in the wrong thread. Any help will be appreciated. Regards.

Ubuntu 6.10 had only support until 2008, and I'm surprised that it work until recent. I doubt there are anyone who support so old system? And if they do, I doublt I would trust them. I mostly use LTS versions who have longer support for security updates. And those are 6.06, 8.04,10.04 and coming 12.04, if you don't want to upgrade every year. I don't like the recent Ubuntu. In my main-system are 10.04, and the different between 6.06 are quite small, I think. The 'revolution' to Unity and Gnome3 are a big step, so compare 6.10 with the recent are not fair. 10.04 (that i use on my main computer) are quite similar to 6.10. I think. So my advice are to install at least 10.04. Just now I try to migrate to Lubuntu, just to avoid Gnome3 and Unity, because 10.04 loose support next year.

---

### Post by AlexDudko on 2012-03-07
> **Azyx said:**
> I wonder what the diffence are between Software center and Synaptic? I have notice that software center are not able to find 'gnome-session-fallback' or indicator-multiload in the software central.

And on the contrary, synaptic is unable to find skype.

---

### Post by Azyx on 2012-03-07
> **AlexDudko said:**
> And on the contrary, synaptic is unable to find skype.

No, I find it on both 10.04LTS and on Lubuntu 11.10 :) 

/Cheers

---

### Post by AlexDudko on 2012-03-07
Strange I don't see it in Synaptic, only a pidgin skype plugin. But I find it with both Software Centre and aptitude.

---

### Post by Azyx on 2012-03-07
> **AlexDudko said:**
> Strange I don't see it in Synaptic, only a pidgin skype plugin. But I find it with both Software Centre and aptitude.

Yes it very strange. But I now know why^^ I have a 64-bit Ubuntu-version also and if I make a 'quick seach' I don't find skype, but if a make a real seach, I get skype.i386 ^^

---

### Post by markbl on 2012-03-07
> **bfengineer said:**
> In my Ubuntu 6.1 (Which I actually like more than the new one) the synaptic package manager has stopped working.
Actually, it stopped working in April 2008. See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases). Wait for 12.04 which will be released in a few weeks.

---

### Post by devinwhite717 on 2012-03-16
Call me old-fashioned but I prefer synaptic easy to use and powerful

---

### Post by Helen McCall on 2012-03-16
I've been using Debian based systems for all my computing since 1996. The original package selection tool was the text based dselect which was an enormous improvement on anything I had used before. Then Debian introduced Apt with aptitude as the package selector which improved things even more. And finally Debian produced Synaptic which made package management extremely easy even when using ppa's and backports etc.

I was horrified when I first encountered Ubuntu Software Centre because of the difficulty of searching for packages, the lack of original package names in the descriptions, and general lack of information presented. I also found that the so-called "reviews" were sometimes giving entirely misrepresentative information.

I took the first opportunity to revert back to using synaptic.

---

