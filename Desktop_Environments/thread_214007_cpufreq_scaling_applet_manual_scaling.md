---
title: "cpufreq scaling applet: manual scaling"
date: 2006-07-12
forum: Desktop Environments
---

### Post by RikoW on 2006-07-12
Hi everyone,

I'm running Ubuntu on a Dell Lat D600 and most things work just fine out of the box. However, I'm not able to set the cpu speed with the cpufreq scaling monitor. I seem to remember, that under breezy I could click on the applet and get a choice of frequencies to select. When I now click on the applet, I don't get anything.

What could be the problem?

Thanks,

              Riko

Edit: It does show the clock speed properly, though ....

---

### Post by Ramses de Norre on 2006-07-12
```
sudo chmod +s /usr/bin/cpufreq-selector
``` now you should be able to right click and choose your frequencies.

---

### Post by RikoW on 2006-07-12
I thought it would be a problem with permission! :)

Thanks! Works as expected again. :)

Cheers,

            Riko

---

### Post by adam.tropics on 2006-07-12
I had the exact same problem a little while ago with the same fix. But am curious why the permisions are set like that by default. Accident, or some good reason?

---

### Post by T-One on 2006-11-15
Just a note: This works great for those of us using VMWare guests on Ubuntu...helps out immensely with ACPI states set to low for VMWare to run efficiently.

Just do the hack above, and set the governor to your liking ( I use performance, but ondemand works as well). Enjoy your faster VM guest!

---

### Post by dannyboy79 on 2006-11-15
could some1 explain what this actually does? i don't use vmware so would it even give me a performace increase by manually setting the freq of the cpu? could anyone explain? what is the freq anyway?

---

### Post by T-One on 2006-11-15
> **dannyboy79 said:**
> could some1 explain what this actually does? i don't use vmware so would it even give me a performace increase by manually setting the freq of the cpu? could anyone explain? what is the freq anyway?

If you have a fairly recent Intel (circa Pentium III, Centino or newer) or AMD (circa Athlon or newer) processor, chances are your CPU supports Frequency Scaling.  If your CPU is rated at, say, 2Ghz, scaling allows the CPU to dynamically "scale"  down and up, depending on the load needed.

If you're not touching your computer, the CPU will scale down to 800Mhz to save power and create less heat. When you start to run something intensive, it will automatically scale back up to its rated max speed, or somewhere in between.

What we're discussing in this thread is the CPUFreq software and kernel modules/Gnome applet which allow the user to control that scaling.

I simply mentioned that the post above which re-enables controlling the settings from the Gnome Applet actually helped me solve ACPI scaling issues I noticed when running VMWare. It can also do the same if you notice some of your programs run really slow.  

Are you up to speed now? ;)

---

### Post by dannyboy79 on 2006-11-15
i guess so, i have a pentium 4 celeron 2.66ghz. would I benefit somehow from using this applet to mess with my scaling? if so, what would i do to take advantage of this?

---

### Post by T-One on 2006-11-15
> **dannyboy79 said:**
> i guess so, i have a pentium 4 celeron 2.66ghz. would I benefit somehow from using this applet to mess with my scaling? if so, what would i do to take advantage of this?

If you're not noticing anything slow, don't sweat it. If you want your CPU to run a bit faster at all times (or have a better scaling policy), do this:

Right-click the Gnome Panel, choose "Add to Panel..."
Select the "Cpu Frequency Scaling Monitor"
You'll see an icon on your panel of a CPU chip with a little bar graph next to it.

Let it set for a few seconds without doing anything. If the bar graph drops and the text next to it reads "800Mhz" ( or something like that), then you have scaling enabled. Next, launch a heavy app, like OpenOffice.org and see if the graph jumps up to 2.66Ghz.

Now, to control that scaling, you can apply the hack that Ramses de norre suggested:

Open a terminal and paste this in:
[quote=Ramses de Norre]```
sudo chmod +s /usr/bin/cpufreq-selector
``` [/quote]

Next, LEFT-click the icon for the CPU Frequency Scaling Applet. You should see two menus: "Frequencies" and "Governors"

The choices under "Frequencies" allow you to choose and lock a particular CPU speed. The choices under "Governors" allow you to choose a scaling profile. 

  [Google Search CPUFreq]("http://www.google.com/search?q=cpufreq&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a") for more information.

---

### Post by Myk0n on 2006-11-19
> **RikoW said:**
> Hi everyone,

I'm running Ubuntu on a Dell Lat D600 and most things work just fine out of the box. However, I'm not able to set the cpu speed with the cpufreq scaling monitor. I seem to remember, that under breezy I could click on the applet and get a choice of frequencies to select. When I now click on the applet, I don't get anything.

What could be the problem?

Thanks,

              Riko

Edit: It does show the clock speed properly, though ....

By the way.. What does the '-s' flag do?

Thanks, Myk0n.

---

### Post by Azriphale on 2006-12-12
the +s flag to chmod sets the application to be run in SUID mode (or Setuid -- set user ID). It means that the Gnome CPU Frequency monitor applet will run with elevated permissions without any further intervention, allowing you to set the frequency as your normal user (where usually only root would be able to do that).

---

