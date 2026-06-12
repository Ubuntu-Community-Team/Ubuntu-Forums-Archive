---
title: "How do I set processor affinity?"
date: 2009-03-19
forum: General Help
---

### Post by gamelord12 on 2009-03-19
I just installed Unreal Tournament, but I have a Core 2 Duo, and it runs twice as fast.  I've seen this problem before plenty of times in Windows, and I know you fix it by setting the processor affinity to only one core.  How do I do this in Linux?  Once that's resolved, is there any way to set it to launch like that every time?

---

### Post by sdennie on 2009-03-19
You will need to use schedtool.  Then the syntax should be:

```

schedtool -a 0x1 -e name_of_your_command

```

---

### Post by Nano_ext3 on 2009-03-19
Nice suggestion Sdennie, I saw this and remembered how useful this will be for my Quad Core :)

_Nano

---

### Post by gamelord12 on 2009-03-20
Could you explain each of the parameters for that command, so I know what it is I'm doing?

---

### Post by sdennie on 2009-03-20
You will probably want to check the man page for schedtool as it explains the options and gives examples on how to use the tool:

```

man schedtool

```

---

### Post by gamelord12 on 2009-03-20
I ran that command exactly and the game still runs too fast.  The man page says at the bottom that knowledge of how the kernel handles processor affinity is needed.  Am I screwed?  Also, I realized that during the installation of UT, I had to mount my Desktop.  Now it's changed to read-only and only has root permissions.  How do I fix this?

---

### Post by gamelord12 on 2009-03-21
I solved the problem with mounting my desktop, but even after trying schedutils, I have the same problem with UT.  I ran it in the terminal with both commands and got no error messages concerning processor affinity.

---

### Post by The Cog on 2009-03-21
I fixed ut this way:

Install package **cpufrequtils**

Make sure you can run /usr/bin/cpufreq-set from your normal user account. This involves either making the program setuid (sudo chmod +s /usr/bin/cpufreq-set) or edit the sudoers file so you can run it without a password prompt. The latter is probably more secure in theory, but harder to set up.

Create a file called ut in /usr/local/bin with these contents:
```
#!/bin/sh
/usr/bin/cpufreq-set -g powersave
/opt/ut/ut
/usr/bin/cpufreq-set -g ondemand

```

Make the script executable: ```
sudo chmod +x /usr/local/bin/ut
```

This fixes the CPU in powersaving mode while UT is running. It seems to work for me. Start the game with the command **ut**.

---

### Post by gamelord12 on 2009-03-22
I've never written a script before, could you explain it line-by-line?  Also, when scripting, since /usr/bin is in my system path, is it necessary to prefix the command with the entire path in a script?

---

### Post by gamelord12 on 2009-03-22
Also, I tested the command, and it does need administrative permission, but putting it in powersave mode doesn't remedy the problem anyway.  I feel like setting processor affinity of a process should be easier than this in 2009.

---

### Post by gamelord12 on 2009-03-25
Anyone?

---

### Post by The Cog on 2009-03-25
Sorry for the delay - busy time for me.

As for the script, just create a text file and then make it executable using the chmod command that I gave.

A nice text-based utility that can set affinity is **htop**. Just arrow down to the process and type an 'a'. I doubt that will fix your problem though - I think that UT is single-threaded, and I know I had speed issues on my single-CPU machine. 

I came to the conclusion that the CPU was switching to the higher clock rate as soon as the game got going and mucking up the timing loop. I guess the game timing calibration was happening before the clock change. And I possibly remember that fixing my clock rate at the higher speed didn't help, so maybe it's more a case of UT just not being able to calibrate with really fast CPUs. In which case you may be really screwed. My PC switches between 1 and 2 GHz which is slow by todays standards.

But of course, that's just how it went on my PC. Things may be entirely different for you.

---

### Post by gamelord12 on 2009-03-27
Well, why does it run okay in Windows on roughly the same speed processor?

---

### Post by rizzeh on 2009-03-28
> **sdennie said:**
> You will need to use schedtool.  Then the syntax should be:

```

schedtool -a 0x1 -e name_of_your_command

```


thank you

---

