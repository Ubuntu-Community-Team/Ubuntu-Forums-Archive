---
title: "X changed virtual terminal to number 9 instead of 7??"
date: 2009-04-15
forum: Desktop Environments
---

### Post by except on 2009-04-15
I'm new to Ubuntu, I just installed version 8.10, and did a few fun things like activate compiz fusion and desklets and whatnot.
I have a Samsung X460 laptop and the brightness control of the screen doesn't work, so I downloaded this little script that does it by writing directly to the LCD driver (or something). This used to work brilliantly.

The script looks like this:

#!/bin/bash
gksu chvt 2
echo 60 |sudo tee /proc/acpi/video/NVID/LCD/brightness
sudo chvt 7

As said, this worked okay for 5 days or so. However ever since today (I don't know what was changed), it doesn't come up with the screen anymore and I have to switch to terminal 9 instead of 7. How do I change X back to running on terminal 7 instead of 9... as this is kind of weird.

Thanks!

---

### Post by PacSci on 2009-04-15
A better question is, why do you need to change TTYs to activate this? Theoretically, you could replace the same script with just:

```
#!/bin/sh
if [ "$1" ]; then
  BRIGHT=$1
else
  BRIGHT=60
fi
echo $BRIGHT | sudo tee /proc/acpi/video/NVID/LCD/brightness
```

Using "gksu" to change terminals just to run a command is redundant. (This script also has the advantage that if you run it as "sh brightness.sh 100", you can change it to 100 instead of 60.)

Of course, this still might not work. But based on what the command looks like, I'd say that there's a pretty good chance.

---

### Post by except on 2009-04-16
Hi Pacsci,

Thanks for your answer. I did not write the script, I'm not very proficient yet with Linux. I do not know why it's made the way it is. However, I have tried your script, and it does nothing at all, while the original script does change the screen brightness, except that it returns me to a virtual terminal (7) which does not seem to do anything at all... the screen is black, there's no prompt and I can type whatever I want but nothing happens. This did not use to be the case. I'm not sure how things changed, but something did to make run its output on TTY 9, while TTY 7 is sort of dead.

I also don't know why the original script works, while yours doesn't. Perhaps the changing of TTY's is required to be able to write to the screen directly from the bash shell, it might not work when done from the graphical environment.

---

### Post by except on 2009-04-16
I added a 'gksu chvt 2' before your script and a 'gksu chvt 7' after it. That makes it work. Somehow it's back to the 7 terminal... I have no idea why it keeps switching back and forth. Also I am seeing a login prompt each time I execute it... probably the prompt of TTY 2.
Is there any reason to do a gksu before you execute the script and only a sudo at the end?

---

