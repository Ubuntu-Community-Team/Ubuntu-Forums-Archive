---
title: "CPU underclocked?"
date: 2009-05-24
forum: General Help
---

### Post by Sentience on 2009-05-24
I dont really understand it, but according to the program Sysinfo my CPU, AMD Turion(tm) 64 Mobile Technology ML-32, which is supposed to be 1.8 Ghz is only showing up as 800 mghz. Also, my computer has been running slower. WTF is going on?

       This is a Compaq Presario netebook, and I didnt think the bios would allow for overclocking, but is there a way to fix whatever happened? While we are on the subject, is there actually a way to overclock, working around the bios? Mostly I just want to get performance back to how it was. 

       Ive been using a bittorent client since this all happened.

---

### Post by DeMus on 2009-05-24
> **Sentience said:**
> I dont really understand it, but according to the program Sysinfo my CPU, AMD Turion(tm) 64 Mobile Technology ML-32, which is supposed to be 1.8 Ghz is only showing up as 800 mghz. Also, my computer has been running slower. WTF is going on?

       This is a Compaq Presario netebook, and I didnt think the bios would allow for overclocking, but is there a way to fix whatever happened? While we are on the subject, is there actually a way to overclock, working around the bios? Mostly I just want to get performance back to how it was. 

       Ive been using a bittorent client since this all happened.

Ubuntu has a build-in system to "underclock" the cpu to make it less warm and use less energy, especially when running on batteries. This is nice.
Don't worry, as soon as you need more power, the frequency will go automatically to give you the power you need.

---

### Post by Sentience on 2009-05-24
My computer has been freezing lately and loading slower. Do you think there is a problem and its not giving me as much power as I need? Do you think the chip is too warm so it wont give it full power?

Can I turn this option off? I am not running on batteries. I would like to know how to turn it back on in case I do take my laptop out, but Im using it like a desktop replacement and want full power to the CPU so it doesnt freeze and take forever to load.

---

### Post by DeMus on 2009-05-24
> **Sentience said:**
> My computer has been freezing lately and loading slower. Do you think there is a problem and its not giving me as much power as I need? Do you think the chip is too warm so it wont give it full power?

Can I turn this option off? I am not running on batteries. I would like to know how to turn it back on in case I do take my laptop out, but Im using it like a desktop replacement and want full power to the CPU so it doesnt freeze and take forever to load.

I switched it off in BIOS, have no idea at the moment in which menu or what it is called exactly. Just re-boot, enter BIOS (probably by pressing F10 since you have a Compaq) and look for a text which indicates CPU frequency scaling. Be careful not to change other items because it might cause your system to not boot anymore.

---

### Post by Sentience on 2009-05-24
I dont think Compaq allows you to mess with the bios for the CPU by default on laptops, unless there is a way to hack it. 

If its something in the OS that is causing my CPU to underclock, shouldnt I be able to turn it off with the command line?

---

### Post by robert shearer on 2009-05-24
I am not at my Ubuntu compy so this is from memory, to display the cpu state right click on an empty part of the top panel and from the menu that opens select 'add to panel '.

From the window that opens scroll down to something like 'cpu frequency scaling applet' and select and add this.

It will appear in the panel and in future as you run applications it will show how Ubuntu adjusts the cpu frequency as required.

Generally it is in an "on-demand' state that saves the batteries and reduces heat for laptops. I still find it useful for my desktop.

---

### Post by Sentience on 2009-05-24
Thanks. That did the trick.

For some reason it was NOT giving me the extra power when I needed it. Very cool that I can extend the battery life this way, but not so cool that my applications were freezing without the extra power kicking in. I think it needs some work.

---

