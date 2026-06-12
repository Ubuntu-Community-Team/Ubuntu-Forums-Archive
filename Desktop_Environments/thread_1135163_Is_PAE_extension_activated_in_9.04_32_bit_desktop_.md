---
title: "Is PAE extension activated in 9.04 32 bit desktop kernel ?"
date: 2009-04-24
forum: Desktop Environments
---

### Post by stack445 on 2009-04-24
Hi all, i soon gonna have to get a powerfull workstation for work, and wanted to know if PAE is compile by default now in the 9.04 32 bit desktop kernel. The logic beeing that even for desktop use, it's not over the top to think someone could be having 6 to xxx gig of ram ? 

The worstation is going to be used for to setup personnal vm to make some test ( no need to go full esx vm kind of setup ) and to use for IPS alarm analysis. 

I would rather keep windows out of the loop for the hosts OS, so if not, what do you recommend.

thank you.

---

### Post by 2061.shy on 2009-04-27
maybe this could help
[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)
its title is:
"32 bit ubuntu with 4GB+ of memory"

---

### Post by mcduck on 2009-04-27
> **stack445 said:**
> Hi all, i soon gonna have to get a powerfull workstation for work, and wanted to know if PAE is compile by default now in the 9.04 32 bit desktop kernel. The logic beeing that even for desktop use, it's not over the top to think someone could be having 6 to xxx gig of ram ? 

The worstation is going to be used for to setup personnal vm to make some test ( no need to go full esx vm kind of setup ) and to use for IPS alarm analysis. 

I would rather keep windows out of the loop for the hosts OS, so if not, what do you recommend.

thank you.

No, it's not enabled in the normal kernel. Use the server kernel if you want PAE without compiling the kernel yourself.

---

### Post by jaygo on 2009-06-08
and [vote for it]("http://brainstorm.ubuntu.com/idea/11653/") :)

I found the server kernel to be significantly slower for desktop usage.

---

