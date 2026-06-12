---
title: "weird firefox problem"
date: 2005-03-21
forum: Desktop Environments
---

### Post by danip on 2005-03-21
Anyone have this problem?  When I start firefox from the applications menu or in terminal it starts up fine but if i put firefox into my gdesklets starterbar it loads up [www.whatuseek.com](www.whatuseek.com).  Any ideas on this problem

---

### Post by bored2k on 2005-03-21
[QUOTE=danip]Anyone have this problem?  When I start firefox from the applications menu or in terminal it starts up fine but if i put firefox into my gdesklets starterbar it loads up [www.whatuseek.com](www.whatuseek.com).  Any ideas on this problem[/QUOTE]
 I would put my money on Adware . What extensions have you installed on Firefox?

---

### Post by cdhotfire on 2005-03-21
go to properties of your firefox icon. Look at the command, then take off %u.  That should do it. 

Try putting %u in ur search bar, should send you to whatyouseek.

edit: this only happens with gdesklets, if you change command to regular icon and put %u, it will not send you to whatuseek.

---

### Post by danip on 2005-03-22
awesome that did it 

Isnt adware for that silly windows operating system?

---

### Post by cdhotfire on 2005-03-22
yes, dont listen to him.

edit: nah im kidding, he knows more than me.:cry:

edit again: you may get adware from extensions you may use, that send to different sites.

---

### Post by wmcbrine on 2005-03-22
It's not adware. There is none yet that affects Linux.

What it is, is this: You're passing "%u" to Firefox, and it interprets that as an address. Since it's not a proper domain name, it does a Google "I'm feeling lucky" search, which in this case yields whatuseek.com.

When invoked from gdesklets, "%u" is apparently not being parsed, but passed unchanged. Presumably, in other locations, it *is* being parsed, and replaced with whatever it's supposed to be replaced with.

---

### Post by gasparov on 2005-04-02
[QUOTE=wmcbrine]It's not adware. There is none yet that affects Linux.

What it is, is this: You're passing "%u" to Firefox, and it interprets that as an address. Since it's not a proper domain name, it does a Google "I'm feeling lucky" search, which in this case yields whatuseek.com.

When invoked from gdesklets, "%u" is apparently not being parsed, but passed unchanged. Presumably, in other locations, it *is* being parsed, and replaced with whatever it's supposed to be replaced with.[/QUOTE]
 That is the mozilla fundation way to make money,it doesn't concern linux or firefox itselfs, on warty I used to have hoover.com if firefox was invoked with %s,it's a soft built in adware in firefox....

---

