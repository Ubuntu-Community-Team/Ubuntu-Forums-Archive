---
title: "Custom Hardware Shutdown Button Action"
date: 2008-12-30
forum: General Help
---

### Post by genericnumber1 on 2008-12-30
I know this is an incredibly odd question, but is there any way I can run a shell command when the computer's power button is pressed instead of one of Ubuntu's default 4 actions selectable from power management?

If you wonder "why would anyone need this?"...
The computer is hooked up to nothing but LAN and a monitor and I control the keyboard/mouse through the remote desktop program synergy. Occasionally I need to run to command to reconnect the computer, but I need to do it enough to where starting ssh, logging in, and running the command can be tedious. I never use the power button, and because it is the only input on the case that the operating system is notified about, it's really the only candidate for this task.

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Can't you just run a script for your command and ssh so that they start when you log in?

---

### Post by hansdown on 2008-12-30
Hi genericnumber1.

Go to system> preferences> power management. Click on general. Under "when power button is pushed"' coose shutdown.

---

### Post by genericnumber1 on 2008-12-30
@Sin:
Yes, I can start synergy and ssh on boot (and I do). But if, for instance, I do not log into the main computer and start the synergy server quickly enough, the synergy client will take a minute or so to connect. The reason for this is because the way the client connects is it increases retries exponentially 1s, 3s, 5s, 15s, 1m, 3m, etc. Because of this, it is often faster to SSH in to make the synergy client connect. To avoid having to SSH in every time I boot, it would save time to just hit the button on the computer case.

@hansdown:
I'm aware that's what I'd do if I wanted the computer to shut down, but that's not my goal.

I realize if this is a extremely difficult goal to accomplish, just tell me so and I'll continue to do it over SSH. :D

---

### Post by happyhamster on 2008-12-30
- If the machine uses acpi to handle powermanagement stuff then you could try modifying the file:

/etc/acpi/powerbtn.sh

- or:

/etc/acpi/events/powerbtn

---

### Post by genericnumber1 on 2008-12-30
> **happyhamster said:**
> - If the machine uses acpi to handle powermanagement stuff then you could try modifying the file:

/etc/acpi/powerbtn.sh

- or:

/etc/acpi/events/powerbtn

I'll give that a try, thanks!

---

### Post by genericnumber1 on 2008-12-30
Hm, it seems even though acpi is enabled, the power button event is directly passed to the gnome-power-manager instead of going through /etc/acpi/events/powerbtn as any modifications I make to powerbtn.sh or events/powerbtn have no effect on the power button logic. Not even changing the event action to /bin/true stops the gnome-power-manager from handling the event. Oh well, I suppose I'll have to just do it from ssh unless anyone knows anything else I can try. Thanks for all the help you all have given so far!

---

