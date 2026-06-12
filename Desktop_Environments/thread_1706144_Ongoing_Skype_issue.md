---
title: "Ongoing Skype issue"
date: 2011-03-13
forum: Desktop Environments
---

### Post by damianburrin on 2011-03-13
I have an issue with skype crashing on startup - this seems to be quite common and i have a part solution but could do with some further help.

As read the following does partly solve the problem
[B][I]sudo chmod ugo-r libpulse.so.0.12.2
sudo chmod ugo-r libpulse-simple.so.0.0.3[/I][/B]

however this kills the audio controls for the entire netbook.  It would appear from reading that downgrading the ia32-libs library or fixing them to a specific version sorts the problem but i see no reference to ia32-libs within synaptic package manager.


The version of Ubuntu i'm running is 10.04 NBR as downloaded from the unbutu site.  uname -a gives it specifically as **2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 GNU/Linux **which would suggest that it's a 64bit version (though i thought the Atom was a 32 bit and i'm sure the download said I386?)


How do i add/update or fix the ia32-libs library as it doesn't appear in synaptic pacakge manager?


Any help really appreciated.


Thanks
Damian

---

### Post by ajgreeny on 2011-03-13
If you start skype at login try a delay of about 10 - 20 seconds before starting it with the command in the startup applications list bash -c "sleep 10; skype" in place of the simple skype command.

It solved a lot of problems for me with skype and with a few other apps, like conky for example.

---

### Post by damianburrin on 2011-03-13
>ou start skype at login try a delay of about 10 - 20 seconds before  starting it with the >command in the startup applications list bash -c  "sleep 10; skype" in place of the simple >skype command.

I had originally put it down to this and don't start skype on start-up and still have these issues.

thanks
Damian

---

