---
title: "Use only windows boot manager or GRUB"
date: 2012-05-19
forum: Desktop Environments
---

### Post by demon68 on 2012-05-19
Hi!
I installed Kubuntu with wubi, and now first I need to choose between starting windows 7 or Kubuntu in the windows boot manager, then I choose between Kubuntu and Kubuntu recovery in Grub. My questions: is it possible to only use one of the boot managers? I'd also like to change the default to Kubuntu from Windows. Also, I'm not sure if that's normal, but Grub doesn't have a black background, but a light grey one with white letters on it, I'd like to change that too.

---

### Post by wilee-nilee on 2012-05-19
> **demon68 said:**
> Hi!
I installed Kubuntu with wubi, and now first I need to choose between starting windows 7 or Kubuntu in the windows boot manager, then I choose between Kubuntu and Kubuntu recovery in Grub. My questions: is it possible to only use one of the boot managers? I'd also like to change the default to Kubuntu from Windows. Also, I'm not sure if that's normal, but Grub doesn't have a black background, but a light grey one with white letters on it, I'd like to change that too.

With a Wubi the windows bootloader is your only choice, grub in the mbr will not work. Don't choose windows either from the grub menu after choosing ubuntu from the windows boot menu.

As far as grub backgrounds not sure, wubi is not using a full grub setup, it is basically a file in windows no partitioning so it is different, than a install to a partition from a booted cd or thumb.

---

### Post by demon68 on 2012-05-19
Thank you for your quick answer. So if I'm stuck with windows boot manager, is it possible to just bypass the Grub, and start Kubuntu after I select it in the boot manager? (in the grub I can choose from 'Kubuntu' and 'Kubuntu recovery' only, I always choose normal Kubuntu) Also can I change the windows boot manager, and make Kubuntu the default system?

---

### Post by wilee-nilee on 2012-05-19
> **demon68 said:**
> Thank you for your quick answer. So if I'm stuck with windows boot manager, is it possible to just bypass the Grub, and start Kubuntu after I select it in the boot manager? (in the grub I can choose from 'Kubuntu' and 'Kubuntu recovery' only, I always choose normal Kubuntu) Also can I change the windows boot manager, and make Kubuntu the default system?

Not that I know of, basically with a dual boot of windows and Ubuntu it is a chain load form one bootloader to the other, so you would see the same unless you did a partitioned install of Kubuntu and used easybcd from windows. Easybcd in windows wont do this with a wubi as far as I know.

---

### Post by demon68 on 2012-05-19
Just coming back to say, that I managed to skip the Grub with the tool grub-customizer, and change the boot priority of the windows boot manager with windows tool easyBCD. The delay for starting the default operating system can be edited by both tools too. So now I have 5 seconds in the windows boot manager to select windows, or it loads Kubuntu without a second boot manager. Which is great.

---

### Post by wilee-nilee on 2012-05-19
> **demon68 said:**
> Just coming back to say, that I managed to skip the Grub with the tool grub-customizer, and change the boot priority of the windows boot manager with windows tool easyBCD. The delay for starting the default operating system can be edited by both tools too. So now I have 5 seconds in the windows boot manager to select windows, or it loads Kubuntu without a second boot manager. Which is great.

Cool, the only thing I will say about that, is that is a pretty hacked boot setup, hope it continues to work. If you did a standard partitioned install you would have Kubuntu first in the grub menu, it would default to it.

Make sure you you backup the Kubuntu, in case of failure, it is just a file in windows, and not designed for long term use, but for trying in lieu of a standard install.

Some have used it as longterm though having limitations in being able to do a partitioned install, so just keep it backed up.

If you decide to do a partitioned setup that wubi can actually be transfered to a partition and be a regular install, there is a thread on the forums for that. 

Best of luck, mainly I just wanted to to be aware of options, and not lose the stuff in Kubuntu

---

### Post by demon68 on 2012-05-19
Thanks, I wasn't aware that installing via wubi and liveCD has so many differences. I'm sure my next install will be a partitioned setup.

---

