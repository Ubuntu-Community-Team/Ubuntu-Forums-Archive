---
title: "terminal issue"
date: 2009-04-28
forum: Desktop Environments
---

### Post by Nathan Otis on 2009-04-28
Greetings all,

Today I have been trying to update the "Rockbox" firmware on my iPod in Ubuntu. Normally, I switch over to my wife's windows machine to do this because the last step requires an executable. Somewhere in my misguided terminal use, I think I've changed something. I'm not sure of the terminology. I'd guess it's the directory?

Where I used to open a terminal and it would say:
*nathanotis@nathanotis:~$*

Now it says:
*nathanotis@nathanotis-desktop:~$*

No amount of "cd" or "\" commands seem to get me back to how it was before.

I rebooted at one point, thinking that would "reset" the terminal, and both my upper and lower panels were gone. I couldn't get "alt-f2" to take me anywhere, so I hit "ctrl-alt-f7" and dropped out of the gui where I typed:
*sudo apt-get install gnome-panel*

This brought the panels back upon reboot. My terminal continues to read:
*nathanotis@nathanotis-desktop:~$*

Does this matter? Am I freaking out for no reason?

Thanks in advance!

---

### Post by hictio on 2009-04-28
It seems like you have changed the hostname of your box, that is, the name of.
Open a Terminal, and type:

```

hostname ENTER

```

And please post back what it prints on screen, I bet it will be: 'nathanotis-desktop'; if that's the case, change it its no big deal.

---

### Post by Nathan Otis on 2009-04-28
> **hictio said:**
> It seems like you have changed the hostname of your box, that is, the name of.
Open a Terminal, and type:

```

hostname ENTER

```

And please post back what it prints on screen, I bet it will be: 'nathanotis-desktop'; if that's the case, change it its no big deal.

That's what terminal said exactly. Crazy! Not sure how that happened... But I've changed it back.

Thanks so much!

---

