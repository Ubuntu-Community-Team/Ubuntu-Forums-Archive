---
title: "Weird green borders"
date: 2017-04-03
forum: Desktop Environments
---

### Post by Vincent_Juge on 2017-04-03
Dear all,

I apologize in advance if there already exists a similar thread; if yes, please show me which it is, and I will delete this one.

For the last 10 days I have had problems with my windows borders (which also cover the 3 buttons in the left-upper corner of the window).
Usually when I start my engine I do not have problems, but after some non-deterministic amount of time, I see things like this:

[ATTACH=CONFIG]274416[/ATTACH]

After a few Google searches, I could not identify the causes of this phenomenon, hence here I am: can anybody help me on this matter?
It is OK to work with these ugly borders, but I'd rather get rid of them.

Thank you very much for you help!

---

### Post by RobGoss on 2017-04-04
The only thing I can think of is you might have to change the border in your settings have you tried that?

I use [Gnome tweak tool]("http:// https://apps.ubuntu.com/cat/applications/gnome-tweak-tool/") for all my theme customizations works very well

You might also try changing themes and see if that is better appealing

---

### Post by Frogs Hair on 2017-04-04
Looks like you are using the default theme already . Try the following in the terminal.

```
sudo apt-get install dconf-tools
```

```
dconf reset -f /org/compiz/
```

---

### Post by Vincent_Juge on 2017-04-06
Thank you for your help,

I tried successively what you both suggested. Unfortunately, it did not work.

My personal investigations also led me to believe that there might be some bug in my LibreOffice distribution (the green-border bug appeared exactly when opening a LibreOffice window), yet after having deleted it and restarted my computer the bug finally occurred again.

Of course, if there is black-magic commands that might be useful for knowing the state of my machine and start an inquiry about what's wrong, I will do my best to provide it to you.

Thanks!

---

### Post by RobGoss on 2017-04-06
Did you already try removing LibreOffice and reinstalling it?

---

### Post by vasa1 on 2017-04-06
> **Vincent_Juge said:**
> ...
My personal investigations also led me to believe that there might be some bug in my LibreOffice distribution (the green-border bug appeared exactly when opening a LibreOffice window), yet after having deleted it and restarted my computer the bug finally occurred again.
...
The above is not consistent with the image you provided in your first post. In that image, the green border is around a browser window, not a LibreOffice window.

Do you have NVIDIA graphics?

> **RobGoss said:**
> Did you already try removing LibreOffice and reinstalling it?
Sometimes, it's possible that the user's profile is corrupted. In such cases, "removing LibreOffice and reinstalling it" won't do anything. Removing or purging doesn't affect the user's profile in *~/.config/libreoffice*.

---

### Post by scriber on 2017-04-06
> **vasa1 said:**
> The above is not consistent with the image you provided in your first post. In that image, the green border is around a browser window, not a LibreOffice window.

Do you have NVIDIA graphics?


Sometimes, it's possible that the user's profile is corrupted. In such cases, "removing LibreOffice and reinstalling it" won't do anything. Removing or purging doesn't affect the user's profile in *~/.config/libreoffice*.

I'm betting it is a Nvidia card as I get similar things happening with graphics after coming out of standby, which I now fix by logging out and back in until there's a proper solution.

---

### Post by Vincent_Juge on 2017-04-08
Thank you:

> **RobGoss said:**
> Did you already try removing LibreOffice and reinstalling it?
I did it. As one could expect, it was useless. At least it eliminated a possible origin for the bug (which ade no specific sense but was circumstancial).

> **vasa1 said:**
> Do you have NVIDIA graphics?
Yes. I changed my driver.The bug did not arise in the last 24 hours. I hope that this was the goold solution.

If ever my problem arises again I will come back here. Ohterwise (e.g. in one week) I will mark my problem as solved.

Have a nice week-end!

---

### Post by Habitual on 2017-04-08
> **Vincent_Juge said:**
> Thank you:


I did it. As one could expect, it was useless.Says the "user". No Offense.
Now the PowerUser would shutdown LO and rm or mv their ~/.config/libreoffice

The Admin would do both before making sweeping statements about "useless"

> **vasa1 said:**
> Removing or purging doesn't affect the user's profile in *~/.config/libreoffice*.

New or updated Driver may help, but if it re-occurs, shut down LO and rename ~/.config/libreoffice to say ~/.config/libreoffice.backup
and open LO and have a look.

---

### Post by scriber on 2017-04-09
> **Vincent_Juge said:**
> Thank you:


I did it. As one could expect, it was useless. At least it eliminated a possible origin for the bug (which ade no specific sense but was circumstancial).


Yes. I changed my driver.The bug did not arise in the last 24 hours. I hope that this was the goold solution.

If ever my problem arises again I will come back here. Ohterwise (e.g. in one week) I will mark my problem as solved.

Have a nice week-end!

Well I changed the driver to the new one, 381.09, and everything is back to normal finally after a couple of frustrating weeks !

---

