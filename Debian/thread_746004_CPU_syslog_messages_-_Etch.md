---
title: "CPU syslog messages - Etch"
date: 2008-04-05
forum: Debian
---

### Post by Awayne on 2008-04-05
I run a Debian system and when I'm logged into a terminal the syslogd keeps printing out a message that my CPU is above its temp threshold and that it is running in modulated clock mode. It isn't Debian specific but thought I should post the problem in here. Does anyone know why it is doing this? I know the system gets really hot (which is why half the case has been taken off to provide extra ventilation).

> Message from syslogd@Nazareth at Sat Apr  5 09:49:05 2008 ...
Nazareth kernel: CPU0: Temperature above threshold

Message from syslogd@Nazareth at Sat Apr  5 09:49:05 2008 ...
Nazareth kernel: CPU0: Running in modulated clock mode


Whenever I give it some extra work to do it always comes up.

---

### Post by kerry_s on 2008-04-05
what is the temp?
is your fans on?
what is it's operating temp?
cpu type?
etc...

come on man, you provided nothing to help us help you.

---

### Post by Awayne on 2008-04-05
> **kerry_s said:**
> what is the temp?
is your fans on?
what is it's operating temp?
cpu type?
etc...

come on man, you provided nothing to help us help you.
Specifics don't really matter in this case as it has been a reported problem over a variety of hardware setups and operating systems. But if you need to know:
1: 'Fan working?' Yes.
2: 'Temp?' Should be around 60 - 70c last checked.
3: 'CPU?' Intel Celeron D.
4: 'OS?' Debian GNU/Linux 4.0r3 Etch - STABLE.
5: 'Kernel?' 2.6.18-6-686.

It's using a default install kernel. If I compiled my own it wouldn't have this problem (it was sorted on a Fed machine by a custom compiled kernel), but for stability and testing purposes I want to keep my current default Deb build kernel.

---

### Post by kerry_s on 2008-04-05
well, first thing that comes to mind is the cooling fan thingy properly seated. is this a home built?
perhaps putting some new thermal paste might help.

you say this is a known problem and the fix is compiling the kernel, what is the setting needed for it to function right?

---

### Post by Awayne on 2008-04-05
> **kerry_s said:**
> well, first thing that comes to mind is the cooling fan thingy properly seated. is this a home built?
No, built by a company, of which I will not buy from again (after sending it back for repairs they knocked it and said it was damaged in post, they left screws off the HDD and they put a huge PSU in a small case...).
> **kerry_s said:**
> perhaps putting some new thermal paste might help.
Interesting you should mention that, I was thinking of replacing the CPU for a better one and adding some new cooling fans and or water cooling depending.
> **kerry_s said:**
> you say this is a known problem and the fix is compiling the kernel, what is the setting needed for it to function right?
It wasn't a fix far as I know. I did a Google search for the message as I do with all problems and someone using Fedora (default kernel) had the same issue. He compiled a kernel from source and the messages never appeared. Debian is the only system I get this on (and I think I had it on Fedora 8 at one point). 
I'm looking at new ways of cooling the system but there is no real solution to it for the time being, I just don't know how to tell syslogd not to report it every 5 seconds to my open terminals.

---

### Post by kerry_s on 2008-04-05
okay, i think i get where your going, you just want to disable the messages, the temp doesn't bother you. :)

i think it can be fixed by adjusting the temp threshold to a higher number.

i'll have to look up the command, it's something like
echo 100 /path/to/the/file

i'll get back to you.

---

### Post by kerry_s on 2008-04-05
here's the part, taken here->
[http://www.columbia.edu/~ariel/acpi/acpi_howto.txt](http://www.columbia.edu/~ariel/acpi/acpi_howto.txt)

```

8.4. What are trip points and how do I set them?

   Trip points are set temperatures that, when the system temperature reaches
   them, trigger some sort of action. Typically this can be a change in cooling
   mode,  or  something  more  drastic. The critical cooling mode has two
   predefined trip points. If the system reaches the first one, called the "hot
   point",  Linux will try to put the system into S4 (suspend to disk) if
   possible, and if the temperature passes the second one, called the "critical
   point", Linux will call /sbin/shutdown -h now.

   You can define multiple trip points each with their own cooling policy. If
   you do, they'll show up in /proc/acpi/thermal_zone/*/trip_points like this:
        critical (S5): 100 C
        passive: 97 C: tc1=4 tc2=3 tsp=40 devices=0xcf6b6d80

   You can set critical, hot, passive, and up to 9 active trip points. Here's
   how you do it: echo a string of numbers to
   /proc/acpi/thermal_zone/*/trip_points separated by a colon. These numbers
   are the various trip points in Celsius. NOT IN Fahrenheit! So you *can* echo
   99:80:35:75:60:55:50:45 > /proc/acpi/thermal_zone/*/trip_points to set the
   critical trip point at 99C, the "too hot, suspend now" trip point at 80C,
   the passive trip point at 35C, the first active trip point at 75C, the next
   one at 60C, and so on through the fifth active trip point at 45C, but in
   practice that's a lot of trip points. You probably only need one or two;
   after all, how many extra fans do you have? However, Linux expects to see at
   least 5 values, and if it doesn't see them it throws an error and refuses to
   process the change. So even if your system only does passive cooling, you
   must supply values for active[0] and active[1]. Just set them to 0 if they
   don't make sense for your platform.

   Unfortunately, if you write values to trip_points (at least 5) and these
   other cooling methods are not supported, Linux will not inform you about it.
   It will silently accept the values and move on. On my system I can't even
   reset  the  lone  critical  trip point permitted me; but no errors are
   generated; the only way I can tell is to read the trip_points file again and
   see that it hasn't changed.

```

---

### Post by Awayne on 2008-04-05
Thank you for the help, I really appreciate it. Might help stop these messages long enough for me to get work done (it's a pain to be editing a file only to have messages flood the term). I'll get some new cooling put in it as and when I can. :)

---

### Post by kerry_s on 2008-04-05
> **Awayne said:**
> Thank you for the help, I really appreciate it. Might help stop these messages long enough for me to get work done (it's a pain to be editing a file only to have messages flood the term). I'll get some new cooling put in it as and when I can. :)

i would tell you the exact command, but it's 3:50am and i'm already seeing double. you might want to try some of the other acpi stuff from the manual, like setting the polling_frequency.

i'm pretty sure your problem lies in acpi not functioning correctly, the d processors are crap, so it's probably not giving the right settings for acpi to go on.

anyway good luck and good night.

---

### Post by jdhore on 2008-04-05
I'd recommend getting some cooling or doing something ASAP...60-70C is WAY too hot for even a Celeron D.

---

### Post by kerry_s on 2008-04-05
> **jdhore said:**
> I'd recommend getting some cooling or doing something ASAP...60-70C is WAY too hot for even a Celeron D.

he's fine from 50->95, if it's to hot the computer will shutdown.
for those celeron d's that might be with in the operating range.

this old laptop i use is between 50->70 depending what i'm doing, the average is around 55.

---

### Post by jdhore on 2008-04-05
> **kerry_s said:**
> he's fine from 50->95, if it's to hot the computer will shutdown.
for those celeron d's that might be with in the operating range.

this old laptop i use is between 50->70 depending what i'm doing, the average is around 55.

dude...I have a Pentium 4 Prescott (Basically the Celeron D with more cache and a faster FSB) and on this motherboard at least, the highest it will let me go is before it shuts down is 75C...so he's dangerously close...and his motherboard MIGHT not have the shutdown-on-overheat.

---

### Post by Awayne on 2008-04-05
> **jdhore said:**
> dude...I have a Pentium 4 Prescott (Basically the Celeron D with more cache and a faster FSB) and on this motherboard at least, the highest it will let me go is before it shuts down is 75C...so he's dangerously close...and his motherboard MIGHT not have the shutdown-on-overheat.
I use a Foxconn motherboard, not the best but does the job. Last I checked when I ran Windows it was doing over 70. Small case, huge, hot power supply, case you can fry eggs on. I really don't have a lot of options until I can afford a better fan and some replacement parts. Hence not buying from that company again. Might have hit 80 once, not entirely sure.

---

### Post by kerry_s on 2008-04-05
> **jdhore said:**
> dude...I have a Pentium 4 Prescott (Basically the Celeron D with more cache and a faster FSB) and on this motherboard at least, the highest it will let me go is before it shuts down is 75C...so he's dangerously close...and his motherboard MIGHT not have the shutdown-on-overheat.

your comparing older to newer, newer runs lower performs better.
i remember all d's running around those temp's.

---

