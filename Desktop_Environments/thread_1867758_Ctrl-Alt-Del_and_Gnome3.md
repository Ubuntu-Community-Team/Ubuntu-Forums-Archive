---
title: "Ctrl-Alt-Del and Gnome3"
date: 2011-10-23
forum: Desktop Environments
---

### Post by Finlandia on 2011-10-23
Hi!

I just upgraded to Ubuntu 11.10 with Gnome3.

Earlier, with Ubuntu 11.04 and Unity, when I pressed Ctrl-Alt-Del I got menu with these options:

- Power Off
- Reset
- Log Off
- Suspend
- Hibernate
- Cancel

(Or something like this; I have Ubuntu in Finnish and I'm not really sure what they are in English).

But now, with 11.10 & Gnome: when I press the Ctrl-Alt-Del combination, I will got a menu like this:

- Log Off
- Cancel

In my humble opinion, the earlier style was much better. Can I optimize/modify the menu so I will get - at least - the Power Off option there? Have the Gnome already some settings for this or can I download - for example, via Ubuntu Software Center - the 3rd party additions?

And another thing:

Now, when I click my name on the top right corner, I get a menu and bottom of it is option Suspend. And if I press and hold the Alt key the text will change to Power Off. Can I change that the Power Off option will be the default (without Alt key)?

Thanks beforehand!


-Finlandia

---

### Post by manech on 2011-10-28
You can reactivate the old Ctrl+Alt+Del feature as follows:
```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_1 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_1 "gnome-session-quit --power-off"

```

---

### Post by Finlandia on 2011-10-29
Thanks, solved!

A tip for others with this same problem. You see the 2nd line:

> **manech said:**
> 
 ```

 gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_1 "gnome-session-quit --power-off"
 
```
 
An unknown reason, when I cut and pasted this line, the two minus signs in front of power-off words was replaced with one long dash. (And I pasted the line directly to a terminal window.) But after I manually replaced this sign back to the two minus all was ok.


-Finlandia

---

### Post by butsuriboy on 2011-10-29
Thanks for the help!  I was also annoyed with the new menu change, and think this way is *much* better.  However, is there a way to go back to the same menu as was in 11.04 and before -- the one with different icons for each of the options, and where everything was arranged vertically?  I guess, if possible, I prefer this menu instead.  Thanks again!

---

### Post by Finlandia on 2011-11-03
> **manech said:**
> You can reactivate the old Ctrl+Alt+Del feature as follows:


Hi again;

your answer worked some days perfectly. But during yesterday the log-off menu was replaced with original Gnome menu so after that I have only Log Off and Cancel but not, t.eg, Power Off.

I guess this was happened after an Ubuntu update. Of course I can replace the menu again. But was this happened only one time or will my menu automatically changed to original at least once per week? ... I mean: I can change the menu once or twice but I have not enough interest to do this again and again.

Thanks!


-Finlandia.

---

