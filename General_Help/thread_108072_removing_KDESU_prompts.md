---
title: "removing KDESU prompts"
date: 2005-12-24
forum: General Help
---

### Post by Brando569 on 2005-12-24
is there anyway to remove the kdesu prompts for apps like synaptic and things that make system wide changes other then adding myself to the root group? im the only one that uses my computer and was wondering if there was a way to bypass it or something

---

### Post by aysiu on 2005-12-25
What's wrong with adding yourself to the root group?
If you do that, it should solve your problem (and lessen security).
If you don't, you'll still get prompted (and security will remain intact).

---

### Post by Brando569 on 2005-12-25
thats the problem i was wondering if there was a way to do it w/o lessening security that much...

---

### Post by mlomker on 2005-12-26
[QUOTE=Brando569]thats the problem i was wondering if there was a way to do it w/o lessening security that much...[/QUOTE]

No.  **sudo** was designed to protect the operating system.  The #1 problem with Windows is that viruses/worms have access to everything once they manage to run.  If you leave the default permissions then when linux viruses start becoming common (it's just a matter of time) they will have to prompt you for the password...and that'd be pretty suspicious.

The next version of Windows, Vista, is actually changing over to what Ubuntu is already doing today....password prompts for doing dangerous things.

---

### Post by Brando569 on 2006-01-04
well since linux viruses arent in the near future how can i remove the prompts or make them store the password permanently for certain things (synaptic, system settings, etc...) i know kde has a option for "save password" but it seems like it never works...

---

### Post by Brando569 on 2006-02-05
no1 has any other input on this?

---

### Post by codejunkie on 2006-02-05
[QUOTE=Brando569]no1 has any other input on this?[/QUOTE]
[http://ubuntuguide.org/#usesudowithoutpasswordprompt](http://ubuntuguide.org/#usesudowithoutpasswordprompt)
this link shows how to disable the prompts for passwords as the other posts mentioned it isn't very secure but it should do what your wanting.
edit: that guide was for ubuntu to make it work on kubuntu i hade to change that guide to this 
comment out this line like this
# Members of the admin group may gain root privileges
%admin	ALL=(ALL) NOPASSWD: ALL
change to
# Members of the admin group may gain root privileges
# %admin	ALL=(ALL) NOPASSWD: ALL
and add your user name to the bottom like this
yourusername	ALL=(ALL) NOPASSWD: ALL

---

### Post by Brando569 on 2006-02-05
cool thanks, im on a mid-sized subnetted college network so i dont really worry about security ;) considering most of the ppl here either have no idea about linux or know how to hack it, and those that do i dont really have anything to hide from them :)

---

### Post by Jucato on 2006-02-05
IMHO, sudo works not only to protect your system from viruses, but also to protect it from yourself, too. Those password prompts provide a visual reminder that the action that you are about to take will affect your system's integrity, for better or for worse. I think it just makes sure that you are reminded that you should know what you are doing. Of course, for expert administrators, being prompted like that always could get annoying. But nobody's perfect, so even they might end up messing up sometimes. just my 2 cents. :D

---

### Post by Brando569 on 2006-02-05
i totally agree with what you're saying and im by far no expert admin (hell im not even a decent admin! lol) it just gets annoying sometimes when i wanna do something quick and i always have to type in the password. i have no fear about security since im the only one that uses my computer and am on a smaller subnet of a network.... i wish there was a way that you could disable the prompts for certain programs that i use alot. shouldnt the "keep password" function on kdesu do this? everytime i check it it doesnt remember the password :( this would be great if it worked..

---

### Post by Parkotron on 2006-02-10
kdesu has always been buggy for me. I'm not sure what the reasons are, maybe it just hasn't been given any attention recently, but I've always had problems with it not launching when called or not launching the program it was told to call. Upgrading to KDE3.5 helped some, but I still run into trouble sometimes, especially when using Administrator Mode in KControl.

Personally, I like the prompts for both the protection from others and the protection from myself. Because I have no real security concerns, I just use a very short easy to type password. I makes filling the password prompts much quicker, but even a relatively weak password is much, much stronger than none.

---

