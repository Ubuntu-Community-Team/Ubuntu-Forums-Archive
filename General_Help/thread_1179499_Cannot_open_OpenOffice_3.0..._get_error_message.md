---
title: "Cannot open OpenOffice 3.0... get error message"
date: 2009-06-05
forum: General Help
---

### Post by MikeTheC on 2009-06-05
Hey Folks:

I am having a problem opening any of OpenOffice. I've never ever had a lick of trouble with OO before, and I'm really stumped by this.

The error I get is:

[indent]The application cannot be started. 
The user interface language cannot be determined.[/indent]

What I've tried thus far is to do a complete removal of OpenOffice and all of its parts, a reboot, and then a fresh download-and-install of it through Synaptic Package Manager.

I've also ensured that [font=courier]openoffice.org-java-common[/font], [font=courier]openoffice.org-l10n-common[/font] and [font=courier]openoffice.org-l10n-en-gb[/font] are installed.

Has anyone else seen this, or got a suggestion?

---

### Post by jonobr on 2009-06-05
Hello


When you removed and reinstalled, did you do a purge?

---

### Post by MikeTheC on 2009-06-05
> **jonobr said:**
> Hello


When you removed and reinstalled, did you do a purge?

What specifically do you mean by a "purge"?

---

### Post by hyperdude111 on 2009-06-05
purge is a complete remove. There is some command but i cant remember, try google?

---

### Post by MikeTheC on 2009-06-05
Well, Synaptic offers two different removal options. The standard one leaves config files, etc., intact. The other option removes all of that stuff.

I used the latter option on anything that was a part of OpenOffice (Synaptic automatically handled the process.) I'm guessing the stuff it did the "normal" removal of are items that don't have their own configuration files and therefore couldn't benefit from the "Complete Removal" option.

---

### Post by MikeTheC on 2009-06-05
FWIW, I just ran the default [font=courier]**ooffice -writer %F**[/font] command from a terminal window and got the following error:

[font=courier]** (soffice:6664): WARNING **: unable to get gail version number[/font]

Anyone know what the term "gail" refers to in this context? It's not a separate program as far as I can tell, because I had apt-get try to install it from the repos and it couldn't find any such package.

Thoughts?

---

### Post by jonobr on 2009-06-05
hello

try 

```
sudo apt-get remove --purge OpenOffice.org
```

---

### Post by MikeTheC on 2009-06-05
> **jonobr said:**
> hello

try 

```
sudo apt-get remove --purge OpenOffice.org
```

Nope, still getting the same error.

---

### Post by jonobr on 2009-06-05
Could you post the results of

ls -l .openoffice.org2/
?

Thanks

BTW thats in your home dir and its <dot>openoffice.org2 :-)

---

### Post by newagelink on 2009-06-13
Sorry, OP: I'm a newbie and can't help you. :(

I came here hoping to learn more about the "gail" error message. OpenOffice.org works for me, but I would like for it to work as it should, without any error messages. My code: ```
daniel@daniel-laptop:~/Documents$ openoffice.org readingschedule.xls 

** (soffice:5288): WARNING **: unable to get gail version number
daniel@daniel-laptop:~/Documents$ error - missing word count in dictionary file
Hash Manager Error : 4
``` Looks like I have *three* errors to overcome, but I was hoping that 'gail' thing would be an easy fix. Maybe I'll start a thread on it if no one answers here.

---

