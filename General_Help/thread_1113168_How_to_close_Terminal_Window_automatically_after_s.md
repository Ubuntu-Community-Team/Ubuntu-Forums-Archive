---
title: "How to close Terminal Window automatically after shell script from cron exits"
date: 2009-04-01
forum: General Help
---

### Post by Cain05 on 2009-04-01
I have a cron task set up to run a shell script at a regular interval during the day.  When the script exits the terminal window stays open.  This leads to multiple terminal windows open over time if I don't close them manually.  In the profile preferences for terminal window it is set to close when commands are completed.  If I double click the script and run it that way the window closes when it completes.  I tried putting exit at the end of the script and that doesn't work either.

Any suggestions?

---

### Post by Sub101 on 2009-04-01
Doesn't ```
exit
```

at the end of the script work?

---

### Post by Cain05 on 2009-04-01
Nope.  Tried that as stated above.

---

### Post by kerry_s on 2009-04-01
what terminal? i never have that problem with xterm.

---

### Post by Cain05 on 2009-04-01
The default one from the install.  A quick looks at Synaptic tells me I have gnome-terminal and xterm.  ps says there is a gnome-terminal running so perhaps that's the one I'm using.  If so how do I change it to make xterm the default?

Once the script is done running it says Press ENTER to continue and close this window.

---

### Post by Cain05 on 2009-04-01
I changed the default terminal to xterm yet cron still loads it in gnome-terminal.  Here's the output from:  sudo update-alternatives --config x-terminal-emulator


```

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/xterm
          2    /usr/bin/uxterm
          3    /usr/bin/koi8rxterm
          4    /usr/bin/lxterm
 +        5    /usr/bin/gnome-terminal.wrapper

```

So xterm is now the default.  I'm not sure what the + means by the 5th item but maybe that's my problem.

---

### Post by [o_0] Rob on 2009-06-20
I had the same problem. Add "&& exit" to your cron command instead of just "exit" and it should work.

---

