---
title: "Linux crashes and hardisk spins out"
date: 2009-05-19
forum: General Help
---

### Post by Ceiber Boy on 2009-05-19
Hi

i'm somewhat new to linux, but have liked what i have seen and am pleased to use it. the problem i have is that occasionally ubuntu will freeze and the hardisk light will remain on.

i've tryed leaving it to see of the problem resolves, and i've als tryed the usual get of of jail cards! all to no avail. the laptop i'm using is a HPpavilion ze2000. all the hardware seems to work well, 

the last time it came to a standstill with my hardisk spinning out of control was when i tryed to watch a viseo in Totem movie player, but it has happened in other apps like firefox!

can anyone help please

---

### Post by quixote on 2009-05-19
Which version are you using?  Jaunty?  Intrepid?  What's your system configuration: graphics card, CPU, amount of RAM?  And when you say "all the usual get out of jail cards" can you give us a summary of which ones you mean?  Then when we try to answer your question, it won't just be the stuff you've already tried. ;-)

---

### Post by Ceiber Boy on 2009-05-20
> **quixote said:**
> Which version are you using?  Jaunty?  Intrepid?  What's your system configuration: graphics card, CPU, amount of RAM?  And when you say "all the usual get out of jail cards" can you give us a summary of which ones you mean?  Then when we try to answer your question, it won't just be the stuff you've already tried. ;-)

i'M using ubuntu 9.04, and i've made sure i have all the latest updates.
CPU: Intel(R) Pentium(R) M processor 1.50GHz
Graphics: 82852/855GM Integrated Graphics Device
Memory: 500Mb
i've tryed waiting, [I]Ctrl + Alt + Backspace.

i'm sure you'll need more information, 

thanks for your help
[/I]

---

### Post by paradigm2 on 2009-05-20
> **Ceiber Boy said:**
> i'M using ubuntu 9.04, and i've made sure i have all the latest updates.
CPU: Intel(R) Pentium(R) M processor 1.50GHz
Graphics: 82852/855GM Integrated Graphics Device
Memory: 500Mb
i've tryed waiting, [I]Ctrl + Alt + Backspace.

i'm sure you'll need more information, 

thanks for your help
[/I]

The memory is slightly on the low side.  Do you have swap space, if so, how much?

---

### Post by Ceiber Boy on 2009-05-20
in the System monitor swap '0 bytes (0.0%)' what dose that mean?

---

### Post by BZF on 2009-05-20
[SIZE=1][COLOR=Blue]what i would say to help with the freezing is to increase the RAM to around 1.5gb-2gb[/COLOR][/SIZE]

---

### Post by quixote on 2009-05-20
Ubuntu is supposed to run in 393MB (I think!), 500MB should be okay.  But video + graphics + whatever might use that up real quick, as paradigm2 suggests.  Try running just one thing at a time, and see if it makes a difference.

There's been a jaunty bug reported recently at [tombuntu]("http://tombuntu.com/index.php/2009/05/18/temporary-fix-for-keyboard-not-working-error-in-ubuntu-904/") that the keyboard can lock up.  If you hit ctrl+alt+F3 or any other function key, you're supposed to be able to get control back.  The screen goes black briefly. I haven't tried it myself, but I'm sure I'll need to soon :-?

Sometimes compiz can interfere with things and it helps to turn it off.  (System -> Preferences -> Appearance -> Visual effects)  It's worth trying to see whether that helps. 

Let us know what you find out.

---

### Post by Ceiber Boy on 2009-05-20
> **quixote said:**
> Ubuntu is supposed to run in 393MB (I think!), 500MB should be okay.  But video + graphics + whatever might use that up real quick, as paradigm2 suggests.  Try running just one thing at a time, and see if it makes a difference.

There's been a jaunty bug reported recently at [tombuntu]("http://tombuntu.com/index.php/2009/05/18/temporary-fix-for-keyboard-not-working-error-in-ubuntu-904/") that the keyboard can lock up.  If you hit ctrl+alt+F3 or any other function key, you're supposed to be able to get control back.  The screen goes black briefly. I haven't tried it myself, but I'm sure I'll need to soon :-?

Sometimes compiz can interfere with things and it helps to turn it off.  (System -> Preferences -> Appearance -> Visual effects)  It's worth trying to see whether that helps. 

Let us know what you find out.

on boot up i've looked at the system monitor and it says that i'm using 154Mb of physical memory, if i perform singular tasks then the problem is not as bad. when i try to perform multiple tasks i might as well not bother!

the swap value i have reconfigured from 60 to 100 (assuming Mb). seeing if that helps. i have already turned off the visual effects

this maching come with MS XP home. (its now juel boot) dare i say that XP seems to handle low memory situations well! the purchasing of memory is not an option for this machine, if i wes going to go down that root then i would just buy a new machine!

---

### Post by quixote on 2009-05-20
"swap 0 bytes" does NOT sound good.  Memory allocated to swap should be 1.5 to 2 times your system memory.  Since yours is 500MB, that's at least 750MB, better 1GB.  100MB is too little.  That's most likely the cause of your problem.

---

