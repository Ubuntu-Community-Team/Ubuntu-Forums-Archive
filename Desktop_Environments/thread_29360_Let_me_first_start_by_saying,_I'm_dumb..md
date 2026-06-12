---
title: "Let me first start by saying, I'm dumb."
date: 2005-04-24
forum: Desktop Environments
---

### Post by Social Burn on 2005-04-24
*sigh*

Firstly, I'm sorry if this is in the wrong forum. The main forum is abit unclear, so I didn't really know where to go for questions. I have used the search feature to try and solve my problem, however I don't think this has ever happened before (and if it has, they prolly just reinstalled).

So here goes.

I just built a new PC back in January. This is an AMD machine. I'm a loyal Slackware fan, however I wanted to try and distro that was AMD64 compatible (slack isn't yet). I used an Ubuntu live CD (4.10 I believe), on my old PC and liked it. So here I am, with a fresh install of Ubuntu 5.04.

Let me first clarify that I have read no documentation, and I breezed through the installation process. Sorry, I just got off a greuling 12 hour shift and just wanted to get this done (I gotta work again tomorrow :( ). 

Ubuntu seems nice. However, apparently I was never prompted to set my root password? So I'm sitting here, with no root access. :(

What I need to know:

1) Does Ubuntu do this on purpose? Or did I just accidentally skip it? If so, what is the default root password? 
2) If I skipped it, is there any way you know of that I can change it (I assume not).
3) Sorry for bothering you. I feel like such a nub. I've used Linux for over a year now, you'd figured I'd know to read. I'm kinda strapped for time lately, though. :(

Thanks for your interest.

---

### Post by Nis on 2005-04-24
0) This is the wrong forum.  Only guides and tips should be posted here.  Questions like this should go in [[http://ubuntuforums.org/forumdisplay.php?f=65]Desktop](http://ubuntuforums.org/forumdisplay.php?f=65]Desktop) Support[/url].
1) Ubuntu does not use the root account by default.  sudo is used instead.  If you need to run a command with root access (like synaptic) run it as 'sudo synaptic' and type in YOUR password (not a root password).  If you would like to "become" root for several commands requiring root access run 'sudo -s'.  This is covered many places on the forum, ubuntuguide.org, and the official Wiki and FAQs.
2) If you want to set a password for the root account (and enable it in the process) run 'sudo passwd', put in YOUR password, and then finally put in what you would like root's password to be.
3) No bother at all.  But for future reference it is sometimes quicker to do a few searches than wait for a response.

---

### Post by ed_agamemnon on 2005-04-24
<post removed>

---

### Post by Social Burn on 2005-04-24
Alright sorry.

I just found it out in the user guide. I also noticed the sticky at the top that clearly states:

"THIS IS NOT THE PLACE TO ASK QUESTIONS!"

Sorry again, please delete.

---

### Post by az on 2005-04-24
[QUOTE=Social Burn]Alright sorry.

I just found it out in the user guide. I also noticed the sticky at the top that clearly states:

"THIS IS NOT THE PLACE TO ASK QUESTIONS!"

Sorry again, please delete.[/QUOTE]

It will not be deleted, it was moved.  Your question has been answered.  Is all well?

---

