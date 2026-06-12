---
title: "Kubuntu on PPC G5"
date: 2005-06-26
forum: Desktop Environments
---

### Post by ttrichle7 on 2005-06-26
kubuntu installed quite nicely on my Tecra 9000
laptop, so I thought I would play around with it on my
G5 at home with the Apple Cinema Display.
However when I tried to boot off of the live CD for PPC
kubuntu-5.04-live-powerpc.iso
it hangs with a white screen and the following text..

...ok
opening display /pci@0, f0000000/ATY,
SimoneParent@10/ATY, Simone_B@1_

and then the hard disk begins to race -- and I have to
shut the power off  ](*,) 
I also tried the 'live video=ofonly' -- same result.

does anyone know if the liveCD actually supports the
2.0GHZ twin cpu G5 model -- or am I in unchartered
waters.

TIA
- Todd

---

### Post by virgule on 2005-06-26
I, for one, suggest you stick with OSX unless you have some programming capabilities... then even... If you really want to run Linux on a G5 look up Yellow Dog Linux from Terra Soft Solutions [[www.terrasoftsolutions.com]](www.terrasoftsolutions.com]) They sell G5 with Linux pre-installed, so YellowDog might be a better bet.

---

### Post by ttrichle7 on 2005-06-27
Thanks for your recommendation..

Did you actually get kubuntu installed on the G5 ? and you perfer the other?
because I was aware of yellow dog - but really liked what I saw of kubuntu.

If it is possible I would like to get Kubuntu installed, ideally in a dual boot scenario with MacOSX.

but the first step is of course getting the live CD to work.

---

### Post by cjwatson on 2005-06-27
[QUOTE=ttrichle7]kubuntu installed quite nicely on my Tecra 9000
laptop, so I thought I would play around with it on my
G5 at home with the Apple Cinema Display.
However when I tried to boot off of the live CD for PPC
kubuntu-5.04-live-powerpc.iso
it hangs with a white screen and the following text..

...ok
opening display /pci@0, f0000000/ATY,
SimoneParent@10/ATY, Simone_B@1_

and then the hard disk begins to race -- and I have to
shut the power off  ](*,) 
I also tried the 'live video=ofonly' -- same result.

does anyone know if the liveCD actually supports the
2.0GHZ twin cpu G5 model -- or am I in unchartered
waters.

TIA
- Todd[/QUOTE]
 Try typing 'live-power4' at the boot: prompt, rather than using the default 'live'.

---

### Post by ttrichle7 on 2005-06-28
CJ thanks for the tip.
after powering up and holding the 'C' key down to boot from the live-CD it came up with the boot prompt and then entering 'live-power4' did the trick  \\:D/ 
so I am now thanking you from Kubunutu running on my G5.
btw. it looks great !!

---

### Post by ttrichle7 on 2005-10-25
just installed Kubuntu Breezy 5.10 onto the G5. you need to used the 'live-powerpc64' boot option when installing from the liveCD. thanks to the dev guys for adding that note to the splash screen :) They have fixed the sound drivers and it now recognizes the hw and plays fine, this was broken with the initial 5.04 liveCD. I did get a weird battery warning sign and when I mouse over the battery icon it says 'power source found' not sure why that is. Looks even better than the previous version. and is really fast :D Kubuntu doesn't have that nice ubuntu hardware db utility to send your hw diagnostic feedback back to development. of course that was gnome based, maybe we will see one that works on kubuntu without throwing in all of the gnome architecture :)

---

### Post by ttrichle7 on 2005-10-25
If you have an Apple Cinema HD Display attached to your G5, make sure that you select display characteristics of 1920x1200, which will give you nice clean graphics similiar to MacOSX. otherwise the default is 1024x768 which is great if you have trouble seeing fine print :rolleyes: 

anybody know why it does not find a power source? is that only on the liveCD or also with the native install?

---

