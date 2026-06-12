---
title: "Overclocking CPU inside linux"
date: 2009-05-24
forum: General Help
---

### Post by alberto ferreira on 2009-05-24
Hi, I wanted to overclock my CPU inside linux. I have an AMD Opteron 146. I know that in windows this is possible with nforce so how can I do it with linux?

---

### Post by Legace on 2009-05-24
> **alberto ferreira said:**
> Hi, I wanted to overclock my CPU inside linux. I have an AMD Opteron 146. I know that in windows this is possible with nforce so how can I do it with linux?

Why don't you want to overclock in BIOS?

---

### Post by alberto ferreira on 2009-05-24
Because I wanted to over and underclock the cpu according to the needs to save power, reduce noise and if needed have the juice for the task

---

### Post by DeMus on 2009-05-24
> **alberto ferreira said:**
> Because I wanted to over and underclock the cpu according to the needs to save power, reduce noise and if needed have the juice for the task

Then overclock in BIOS to a value you know your CPU and the rest of the board can handle.
At the same time enable a setting called throttling CPU frequency, or something in that line of words. I don't know the exact phrase.
What will happen is when you don't need a fast system it will go down in frequency, power and therefore also sound of the fan by itself. Whenever you need it it will go up till the value you set. All automatically.

---

### Post by alberto ferreira on 2009-05-30
Thanks but my bios auto-overclocking as needed feature doesn't allow me as much precision and performance as manual overclocking ( believe me as I used that in the past but having the CPU overclocked at 150% is not possible with that option ).

**Please, how do I do it inside Linux?** And please, don't tell me to use the bios because that's not what I'm asking


Thanks

---

### Post by kerry_s on 2009-05-30
a quick google, this 1 looks interesting: [http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/](http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/)

---

### Post by ell02 on 2009-05-30
Perhaps this doesnt belong here,but i recently tried that nv clock package.Soon thereafter i got a 8254 timer not connected to acpid message on boot ups.then came vidio crashes,no monitor on boots ect.. This was with a 8400 card.
Reinstalled jaunty using the noacpid option and so far so good.Dont know if ill try again as i'm really just a duffer poking at things anyhow.

---

### Post by 3rdalbum on 2009-05-30
If they are telling you to use the BIOS and are not suggesting a software-based way of doing it, then it's because they haven't even heard of anyone doing it in Linux. I haven't.

As for lowering noise in your system, just chuck a Noctua fan onto your CPU cooler. Turn off CPU fan control in your BIOS. Noctua fans are very quiet and they don't make more noise when they are running at full speed. I have my Core 2 Duo overclocked to 3.6Ghz full-time with a Noctua fan (uncontrolled) and the whole system is still quieter than it was with the stock Intel cooler (controlled speed).

---

### Post by Yellow Pasque on 2009-05-30
If the Opty 146 is a K8-based CPU, you can use a program called cpupowerd for userspace voltage/clock control.

---

### Post by alberto ferreira on 2009-06-02
Yes it is, can you explain how to use the tools you mentioned? Or give me any reference?

---

### Post by SpawnHappyJake on 2012-03-31
Hi, just doing some Internet cleanup. This thread still comes up in the first search result when one Googles "overclock cpu Linux."

This thread needs a link here: [http://www.overclock.net/t/1205257/overclock-cpu-in-linux-necessary-program-names-given]("http://www.overclock.net/t/1205257/overclock-cpu-in-linux-necessary-program-names-given")

Overclocking of modern CPUs is done by writing to the MSR. The MSR kernel module for Linux lets you do that. And the two tools c2ctl and k10ctl use the MSR kernel module for you in you overclocking endeavors (both are Linux programs).

Cheers,
Jake

---

