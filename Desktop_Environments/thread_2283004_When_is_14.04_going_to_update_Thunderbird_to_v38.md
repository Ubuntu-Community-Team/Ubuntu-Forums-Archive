---
title: "When is 14.04 going to update Thunderbird to v38?"
date: 2015-06-18
forum: Desktop Environments
---

### Post by greg2lapa on 2015-06-18
thunderbird is in the main repo and therefore is supposed to get security updates at a minimum. Thunderbird v38.0.1 was released a week ago but v31.7 appears to be the only thing available.

why isn't Thunderbird updated? Is there a way to check further into this?

---

### Post by wildmanne39 on 2015-06-18
Hi, the best answer is here:
[http://askubuntu.com/questions/151283/why-dont-the-ubuntu-repositories-have-the-latest-versions-of-software](http://askubuntu.com/questions/151283/why-dont-the-ubuntu-repositories-have-the-latest-versions-of-software)

---

### Post by greg2lapa on 2015-06-18
> **Wild Man said:**
> Hi, the best answer is here:
[http://askubuntu.com/questions/151283/why-dont-the-ubuntu-repositories-have-the-latest-versions-of-software](http://askubuntu.com/questions/151283/why-dont-the-ubuntu-repositories-have-the-latest-versions-of-software)

Not applicable because 
1) thunderbird is in main repository
2) security updates get excepted when the app is in the main repo

---

### Post by QDR06VV9 on 2015-06-18
> **Wild Man said:**
> Hi, the best answer is here:
[http://askubuntu.com/questions/151283/why-dont-the-ubuntu-repositories-have-the-latest-versions-of-software](http://askubuntu.com/questions/151283/why-dont-the-ubuntu-repositories-have-the-latest-versions-of-software)
+1

> **greg2lapa said:**
> thunderbird is in the main repo and therefore is supposed to get security updates at a minimum. Thunderbird v38.0.1 was released a week ago but v31.7 appears to be the only thing available.

why isn't Thunderbird updated? Is there a way to check further into this?
If you just have to have the new release there is a ppa for that.
> **Official PPA for Thunderbird Beta**

                                                                          
                                                                    
                                                                   **PPA description**

   
    This PPA contains releases of Thunderbird from the beta channel
 All users of this PPA are encouraged to report any bugs they find. Instructions for reporting bugs can be found at [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs). Please have a read of this before reporting a bug, as it may help save time

   
     
      
                                                                                   **Adding this PPA to your system**

                            You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:mozillateam/thunderbird-next**           to your system's Software Sources.           ([Read about installing]("https://launchpad.net/+help-soyuz/ppa-sources-list.html"))         


it currently has 
[TABLE="class: listing sortable"]
[TR]
[/TR]
[TR]
[TD][/TD]
[TD]1:38.0~b6+build2-0ubuntu0.14.10.1[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD]                 1:38.0~b6+build2-0ubuntu0.14.04.1[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD]                 1:38.0~b6+build2-0ubuntu0.12.04.1                                
[/TD]
[/TR]
[/TABLE]

If it was a security issue then it would be in the main repos!
Regards

---

### Post by grahammechanical on 2015-06-18
Security updates do not necessarily require upgrading the application to a newer version. First of all, newer versions may also have the same security vulnerability. 

Second, waiting for the application's developers to release a newer version would expose the user to risk when a quicker method would be to patch the present version in the repositories and push the patched version as a security update.

I am using Wily Werewolf, the development version of Ubuntu 15.10 and that has Thunderbird 31.7.0 installed. So, it seems that the Ubuntu developers are not in any rush to keep up with developments in Thunderbird. Whereas, Firefox is at version 38. But I never use Thunderbird. Perhaps if I did use it I would have Thunderbird 38. I do not know.

Regards.

---

### Post by jaz013 on 2015-07-23
Yeah, this really needs to become more of an issue.  With the last update to Thunderbird 31.7 it's now totally broken and doesn't work with self-signed TLS sessions.  This was a known issue that was fixed ages ago and Thunderbird 38 works fine.

So until this is updated, no email for me!  Yay!

---

### Post by Guinness2702 on 2015-07-31
> **jaz013 said:**
> So until this is updated, no email for me!  Yay!


  Join the club mate.  I specifically chose the LTS version because I expect it to be supported for five years, and blocking bugs like this to be fixed, but it's literally been months now ... I think more than half a year and Thunderbird is still unusable in 14.04.  I wish I knew what was going on and how to fix this problem.  I really don't want to do a manual install .... this is the kind of basic stuff I'd expect canonical to fix as a matter of urgency .... it's not like this issue only affects a handful of people.  I am losing faith in these people :(

---

### Post by cimmo2 on 2015-08-18
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1476169](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1476169)

---

### Post by duke1995 on 2015-08-27
Thunderbird 38.2.0 has arrived :-).

---

