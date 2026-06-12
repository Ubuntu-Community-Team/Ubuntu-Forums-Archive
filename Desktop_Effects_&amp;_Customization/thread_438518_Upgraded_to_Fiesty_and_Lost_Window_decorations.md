---
title: "Upgraded to Fiesty and Lost Window decorations"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by aldenhg on 2007-05-09
Hi all-
I recently upgraded from Edgy to Fiesty and in doing so I lost Beryl's window decorations. I've already asked about this in a thread on the Open Compositing forums, which can be found here: [http://www.opencompositing.org/viewtopic.php?f=37&t=145]("http://www.opencompositing.org/viewtopic.php?f=37&t=145")
My video card is a Nvidia 7600GS, my proc is a hyperthreaded P4 and my motherboard is an Asus P4P-800D.
Any insight would be greatly appreciated.

---

### Post by Foxmike on 2007-05-09
Maybe you would want to re-install nvidia drivers using the new Closed Source Drivers Manager you can find in the System -> Administration menu?

---

### Post by aldenhg on 2007-05-10
I reinstalled the drivers and tried both the nvidial-glx-new and the nvidia-glx and neither give me the desired results. same for trying the Copy render path.

---

### Post by dannyboy79 on 2007-05-10
a temporary solution is to add metacity to your sessions startup apps. I remember this bandade of a fix for compiz and xgl. I think it has something to with gconf, you need to make sure that you have a default window decoration set within gconf-editor, i think

---

### Post by aldenhg on 2007-05-11
Everything is set up as it should be. I'm fed up with monkying with it for the time being that I'll just use Compiz and wait for Open Comp.

---

### Post by dannyboy79 on 2007-05-11
well this just happened to me also, all I had to do was add metacity to the session startup apps and ALSO make sure you turn OFF auto save session. there's a bug with it. that was the key for me!

---

