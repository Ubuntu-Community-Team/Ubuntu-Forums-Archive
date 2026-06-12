---
title: "Dazuko - What is it"
date: 2007-12-10
forum: Desktop Environments
---

### Post by Geffers on 2007-12-10
I'm running Gutsy on a dual boot machine.

I notice at boot up I get the following warning;

WARNING, dazuko module is not loaded, please insmode dazuko module.

Searching the forums I assume dazuko is something to do with anti virus, I did recently install AVG as I am familiar with this program via Windows.

So, what is dazuko and how do I actually insmode it :)

Geffers

---

### Post by dtgolder on 2008-02-29
Bump--get the same error message...anyone have some help?

(Also have AVG installed, but it's working fine)

---

### Post by Geffers on 2008-03-01
> **dtgolder said:**
> Bump--get the same error message...anyone have some help?

(Also have AVG installed, but it's working fine)

Wow!!

I posted that message in early December last year, your's is the only reply.

Yeah, mine is working fine but the update I have to run with root priviledges otherwise it fails.

geffers

---

### Post by dtgolder on 2008-03-01
I solved the root priv issue...try adding yourself to the AVG group...then reboot. if you do that, then you won't need to run as root.

But it still hasn't really answered the dazuko question--I think it's so that it can scan all the files (rather than return errors on some as it does now) but not sure....

---

### Post by Geffers on 2008-03-01
> **dtgolder said:**
> I solved the root priv issue...try adding yourself to the AVG group...then reboot. if you do that, then you won't need to run as root.

That's an idea, thanks, I'll give it a try.

> **dtgolder said:**
> 
But it still hasn't really answered the dazuko question--I think it's so that it can scan all the files (rather than return errors on some as it does now) but not sure....

Possibly but the error message suggests I inismod dazulo, whatever that is.:confused:

Geffers

---

### Post by sawjew on 2008-03-05
Dazuko is a kernel module that enables on-access scanning of files with anti-virus or similar applications.  If you look [here]("http://ubuntuforums.org/showthread.php?t=52385&highlight=dazuko") you will see how to set up on-access scanning with clamav and dazuko.  Unfortunately to install dazuko on Gutsy requires removing apparmor which is a security component now included in Ubuntu.

You only need dazuko for on-access scanning, AVG works fine for normal scanning.  I only have AVG installed because it is a requirement at work to have antivirus installed.  I really don't use it because it is not really necessary.

---

### Post by Geffers on 2008-03-05
> **sawjew said:**
> Dazuko is a kernel module that enables on-access scanning of files with anti-virus or similar applications.  If you look [here]("http://ubuntuforums.org/showthread.php?t=52385&highlight=dazuko") you will see how to set up on-access scanning with clamav and dazuko.  Unfortunately to install dazuko on Gutsy requires removing apparmor which is a security component now included in Ubuntu.

You only need dazuko for on-access scanning, AVG works fine for normal scanning.  I only have AVG installed because it is a requirement at work to have antivirus installed.  I really don't use it because it is not really necessary.

Thanks, I guessed it may have been something like that as my AVG was working fine.

I assume when you say 'it is not really necessary' that you are referring to Linux not being a virus target.

Geffers

---

### Post by sawjew on 2008-03-05
> I assume when you say 'it is not really necessary' that you are referring to Linux not being a virus target

Yes, that is what I meant.  The only reason you really need antivirus for linux is to protect windows boxes in your network.  I have email virus scanning provided by my ISP so I don't worry about passing on viruses through email either.

---

