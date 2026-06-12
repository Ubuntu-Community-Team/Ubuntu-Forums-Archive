---
title: "Vostro 1500 problem (stemming from no sound issue)"
date: 2008-03-04
forum: Dell  Ubuntu Support
---

### Post by MedellinManDem on 2008-03-04
Hi all,

I am a new Ubuntu user so bear with me. I cannot get any sound on my Vostro 1500. Having tried to solve this problem using the guide found @ [http://linuxblog.pansapiens.com/2007/11/29/ubuntu-gutsy-gibbon-710-on-a-dell-vostro-1500-laptop/]("http://linuxblog.pansapiens.com/2007/11/29/ubuntu-gutsy-gibbon-710-on-a-dell-vostro-1500-laptop/")  

However, I stumble across an immediate problem when I enter the command: 

“apt-get install linux-backports-modules-generic”

What happens when I enter this, is that I receive two messages saying:

"E: Could not open Lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

Does anyone have any ideas what this means?

---

### Post by dicecca112 on 2008-03-04
type sudo in front of that apt-get line, and then when it prompts you for a password, entire the password that you use to login to the system.

---

### Post by MedellinManDem on 2008-03-04
Did that. It then says:

"E: Couldn't find package linux-backports-modules-generic"

---

### Post by MedellinManDem on 2008-03-04
Anyone else?

---

### Post by MedellinManDem on 2008-03-05
I can't believe no one can help on a dedicated Dell/Ubuntu forum...:s

---

