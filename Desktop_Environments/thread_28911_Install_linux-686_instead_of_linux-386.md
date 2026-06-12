---
title: "Install linux-686 instead of linux-386?"
date: 2005-04-22
forum: Desktop Environments
---

### Post by Alexandr on 2005-04-22
Hi, such question.
In advices on postinstall adjustment recommend to install linux-686 instead of linux-386 (for corresponding CPU types). Gives this real advantage or no? Who try?
Thanks.

---

### Post by cowbud on 2005-04-22
If you have the hardware to take advantage of the optimizations there is going to be some gain. If you will notice it or not is another question. Most likely not. It is still good to run versions optimized for your hardware.

---

### Post by Alexandr on 2005-04-22
[QUOTE=cowbud]If you will notice it or not is another question. Most likely not.[/QUOTE]
All clear. Thanks.

---

### Post by bored2k on 2005-04-22
[QUOTE=Alexandr]All clear. Thanks.[/QUOTE]
 In a terminal type
uname -a

If you have a 686 proc, go with 686. Also, 386 doesnt support more than 900MB RAM.

Example of 686 machina:
```
uname -a
Linux noir 2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686 GNU/Linux

```

---

### Post by railz68 on 2005-04-22
I never knew this, and never thought to ask, DOH!

Downloading i686 now.

Just dowloaded i386 last night  :???:


edit, checking US download mirrors, I don't see a "i686" to get. Only see i386.

---

### Post by dewey on 2005-04-22
i686 is still i386 arch, just optimized.  Download and install the i386 version of Hoary, you upgrade the kernel after installation, easiest way is through apt-getting the kernel.
```
$sudo apt-get install linux-686
```

Also, just curious, what Processor do you have?  You could probably optimize further, for instance I use the k7 kernel with my AMD64 3000+.

---

### Post by Alexandr on 2005-04-23
[QUOTE=bored2k]
uname -a
[/QUOTE]
Thanks, I know. :) I have i686.

I has understand so as not to will be essential difference in performance.
And download approximately 20 Mb simply for experiment with modem dialup... :)

Thanks.

---

### Post by Alexandr on 2005-04-23
If this:
[QUOTE=dewey]
Also, just curious, what Processor do you have?[/QUOTE]
to me, that: Celeron 1200 MHz.

---

### Post by jhands on 2005-04-23
just curious, if i install the 686 kernel, will the other software which are 386 like mplayer still work?

---

### Post by MetalMusicAddict on 2005-04-23
[QUOTE=Alexandr]Hi, such question.
In advices on postinstall adjustment recommend to install linux-686 instead of linux-386 (for corresponding CPU types). Gives this real advantage or no? Who try?
Thanks.[/QUOTE]
This is a question Ive asked before and I was told that unless you have everything compiled the same, ie: 686, 386 whatever, I really wont matter.

---

### Post by NaplesBill on 2005-04-23
It tried using the K7 kernel with my Sempron 2200+ and then I tried using the i686 kernel.  There was a very noticable improvement when I switched to the i686 kernel.  I know it doesn't sound right but it is what it is.  Gnome startup is faster, application startup is faster and screen refreshes are much faster.

---

### Post by jhands on 2005-04-23
can any1 point me to a place where i can learn how to install i686 instead of i386?

---

### Post by dewey on 2005-04-23
[QUOTE=jhands]can any1 point me to a place where i can learn how to install i686 instead of i386?[/QUOTE]
I already posted that answer, install hoary 386, and do.
```
$sudo apt-get install linux-686
```

And to your other question about 386 apps, yes they will work.  I'm running mplayer386 on a k7 kernel.

---

### Post by Daz_Man on 2005-04-23
hi, im a complete linux newbie. i have got an AMD 64 3200+ (Clawhammer) cpu and was wondering whether i should install the K7 kernel or the 686 one? i followed the advice of someone who posted earlier saying that he installed K7 kernel for their AMD 64 3000+ so i went ahead and did that. if i shouldnt have done that how do i uninstall it?

also what is different between these 2 kernels and what do they mean? i have seen 386, 586, 686, K7 whilst i have been browsing through forums and i dont have a clue what each one means.

Thanks

---

### Post by Sabator on 2005-04-23
[QUOTE=Daz_Man]hi, im a complete linux newbie. i have got an AMD 64 3200+ (Clawhammer) cpu and was wondering whether i should install the K7 kernel or the 686 one? i followed the advice of someone who posted earlier saying that he installed K7 kernel for their AMD 64 3000+ so i went ahead and did that. if i shouldnt have done that how do i uninstall it?

also what is different between these 2 kernels and what do they mean? i have seen 386, 586, 686, K7 whilst i have been browsing through forums and i dont have a clue what each one means.

Thanks[/QUOTE]
 I think k7 is for AMDs, while 586 and 686 or for Intels.

---

### Post by dewey on 2005-04-23
Use the k7 for AMD64, if you're going to use 32bit.  k8 if you're going 64

386 is the general architecture, used for PCs and such.  Different computers use different architectures, like PowerPC(PPC) is Macintosh and x86_64 is 64bit processors.

386 is the standard, and 686 and k7 are specialized versions of 386, that take advantage of the CPU you're using. Generally, you use 686 for Intel, and k7 for AMD. They provide a speed boost, and for some people it's quite noticeable, and other's don't seem to see any difference.  I always upgrade to the specialized kernel anyway, it's one simple command, so why not?

Any more questions, don't hesitate to ask.

---

### Post by NaplesBill on 2005-04-23
[QUOTE=dewey]Use the k7 for AMD64, if you're going to use 32bit.  k8 if you're going 64

386 is the general architecture, used for PCs and such.  Different computers use different architectures, like PowerPC(PPC) is Macintosh.

386 is the standard, and 686 and k7 are specialized versions of 386, that take advantage of the CPU you're using. Generally, you use 686 for Intel, and k7 for AMD. They provide a speed boost, and for some people it's quite noticeable, and other's don't seem to see any difference.  I always upgrade to the specialized kernel anyway, it's one simple command, so why not?

Any more questions, don't hesitate to ask.[/QUOTE]

That's what I thought too but I definately get better performance from the i686 kernel, even though I have an AMD processor.  I don't get it but I guess it really doesn't matter.

---

### Post by dewey on 2005-04-23
Well, just for informational purposes.  Processors have sets of instructions that they can use, and 386 is the base set of instructions.  When you're using a higher end processor, like a P4 or an AMD Barton, it has extra instructions it can use, and the other kernel versions make use of them, often increasing performance.

---

### Post by NaplesBill on 2005-04-23
I understand the instruction optimizations but I'm still surprised by my experience with the kernel/processor in my system.  

My other computer is a P4 3.06 with HT and it is definately faster by far but for what I'm using my Linux machine for it's overkill.  I built this machine for $125 and the Sempron 2200+ is more than acceptable for internet/music/email and general computing.  I was using the K7 kernel and figured I'd try to i686 to see how much I was gaining from the K7 kernel.  I was shocked to discover that the i686 kernel was faster.  It's definately not my imagination either.

---

### Post by dewey on 2005-04-23
I don't know either, but hey, whatever works.

---

### Post by jhands on 2005-04-24
[QUOTE=dewey]I already posted that answer, install hoary 386, and do.
```
$sudo apt-get install linux-686
```

And to your other question about 386 apps, yes they will work.  I'm running mplayer386 on a k7 kernel.[/QUOTE]
woow, that only took 2 minutes from downloading to installing. now only one question left. can i uninstall the 386 kernel safely from synaptic?

edit:- i uninstalled the 386 kernel but now the internet in 686 doesnt work?Help

---

### Post by Nob on 2005-04-24
[QUOTE=jhands]woow, that only took 2 minutes from downloading to installing. now only one question left. can i uninstall the 386 kernel safely from synaptic?

edit:- i uninstalled the 386 kernel but now the internet in 686 doesnt work?Help[/QUOTE]
 exactly what i was going to ask - do i have to install modem driver all over again?

---

### Post by crazybill on 2005-04-24
I did a **sudo apt-get install linux-686** on an AMD64 machine, but I have not noticed that much performance gain yet... not to say that there isn't any... just haven't noticed it yet. I do not have over the 900MB of RAM that limits linux-386

---

### Post by dewey on 2005-04-24
[QUOTE=crazybill]I did a **sudo apt-get install linux-686** on an AMD64 machine, but I have not noticed that much performance gain yet... not to say that there isn't any... just haven't noticed it yet. I do not have over the 900MB of RAM that limits linux-386[/QUOTE]
On an amd64 machine, try using the k7 kernel.  If you're using 64bit Hoary, use the k8  kernel.

---

### Post by epb613 on 2005-05-02
[QUOTE=Nob]exactly what i was going to ask - do i have to install modem driver all over again?[/QUOTE]
 Me too - is it safe to now uninstall linux-386?

---

### Post by dewey on 2005-05-02
[QUOTE=epb613]Me too - is it safe to now uninstall linux-386?[/QUOTE]

Yes it's safe, but it's always good practice to leave a kernel or two, in case your new one screws up.

Also, you'll have to re-install any kernel modifications you made, graphics drivers, and modem drivers, with every new kernel.

---

