---
title: "Dependencies?"
date: 2009-04-28
forum: General Help
---

### Post by Nyr on 2009-04-28
Hello all,

Yesterday, in order to improve the performance of my Intel card on my laptop (following instructions here: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)), I upgraded to the 2.6.30-rc2 kernel. 

Now, I'm trying to solve another problem with the evdev driver, following the instructions here: [http://ubuntuforums.org/showthread.php?t=974723](http://ubuntuforums.org/showthread.php?t=974723). 

When I try to do sudo apt-get install build-essential libtool automake gcc xorg-dev xutils-dev, however, I get this error message in the terminal: 
[INDENT]"Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created
or been moved out of Incoming. The following information may help resolve the situation:
The following packages have unmet dependencies:
libxfont-dev: Depends: libfreetype6-dev but it is not going to be installed"[/INDENT]

Trying to install libfreetype6-dev also fails, obviously. In Synaptic, I am told that:
[INDENT]"The following packages have unreasonable dependencies. Make sure that all required repositories are added and enabled in the preferences"
[/INDENT]

And I get this error message:
[INDENT] "Depends: libfreetype6 (=2.3.9-4build1) but 2.3.9-4ubuntu0.1 is to be installed"[/INDENT]

My question is: Is it related to the kernel change? (I'd assume so). And how do I fix this dependency issue?

Thanks in advance!

---

### Post by zvacet on 2009-04-28
```
sudo apt-get -f install
```

---

### Post by Nyr on 2009-04-28
Well, I feel dumb. That did it. Cheers!

---

### Post by dcstar on 2009-04-29
> **Nyr said:**
> Well, I feel dumb. That did it. Cheers!

There's nothing "dumb" about it, the system had an unmet dependency that potentially could cause problems if it was installed and told you about it.

Forcing the install anyway may have got the package installed, but at the risk of now having something that has **not** been verified to work correctly.

---

### Post by mc4man on 2009-04-29
> My question is: Is it related to the kernel change? (I'd assume so).

No it was probably because libfreetype6 had a security update yesterday to 2.3.9-4ubuntu0.1,(and  had been installed to your system), but  the matching -dev wasn't available to you for one reason or the other.

While forcing may have worked out it's better to 'research' your version issues first.

generally that type of error for a -dev install

"Depends: libfreetype6 (=2.3.9-4build1) but 2.3.9-4ubuntu0.1 is to be installed"

means libfreetype6 2.3.9-4ubuntu0.1 is installed but libfreetype6-dev 2.3.9-4build1 is what's available in your sources

So a little looking

[http://packetstormsecurity.org/0904-advisories/USN-767-1.txt](http://packetstormsecurity.org/0904-advisories/USN-767-1.txt)

[http://security.ubuntu.com/ubuntu/pool/main/f/freetype/](http://security.ubuntu.com/ubuntu/pool/main/f/freetype/)

---

