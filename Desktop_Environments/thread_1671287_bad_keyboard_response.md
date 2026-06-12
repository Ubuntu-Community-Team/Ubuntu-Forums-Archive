---
title: "bad keyboard response"
date: 2011-01-19
forum: Desktop Environments
---

### Post by Mosabama on 2011-01-19
Hello,

ubuntu doesnt respond to the keyboard very well, I mean while typing it drops some keyboard hits (characters) while typing. and some times it adds a letter that I typed (twice).

what do you think is the problem?

like I had more that 10 mistypes typing this.
now 12 lol.

please help its really annoying.

---

### Post by Mosabama on 2011-02-03
bump

---

### Post by Mosabama on 2011-02-03
up

---

### Post by Mosabama on 2011-02-04
up

---

### Post by Kirboosy on 2011-02-04
Have you enabled Sticky Keys or any sort of Keyboard accessibly  feature?

Those can create strange things.


What kind of computer is it?

---

### Post by Mosabama on 2011-02-04
its toshiba satellite.

 even uninstalled xserver and installed it again.. nothing changed

---

### Post by Kirboosy on 2011-02-04
So even while LiveCDing Ubuntu it still has issues?

---

### Post by Mosabama on 2011-02-04
no, i didnt hve this problem before ... even now some times it works normally but most of the time the problem is there,,,

and some times the problem is there but less buggy

---

### Post by Mosabama on 2011-02-04
I am downloading the new kernel now .. I will tell you the result.

if I want to type this sentence again without correction it would be: lol

I am downlading th new kernelnow Iwill tel you the esult.

---

### Post by Kirboosy on 2011-02-04
This is going to sound strange...but...Are you fast at typing? (Not insulting you, honestly)

---

### Post by Mosabama on 2011-02-04
no not really ... normal

and even if I am fast I didnt hve this prob before.
and I have to be REALLY slow to get what I am typing right. (1 char a second)

---

### Post by Kirboosy on 2011-02-04
Ok. That last part about if you type at 1 word a second answers my question...


I had a similar problem once with my IBM g40 and if I remember correctly it resolved itself with updates or I reinstalled.

---

### Post by Mosabama on 2011-02-04
ok I just found out its not linux problem... its my computer I tried it in windows and its the same thing !!!! I didnt touch bios settings.

anyway I set bios settings to default now. but the problem stays. I think there is something wrong with my hardware.

---

### Post by Kirboosy on 2011-02-04
have you changed the keyboard out lately? Maybe the connector to the keyboard has somehow become loose...that is strange.

Try plugging in a USB keyboard and see if that helps/

---

### Post by Mosabama on 2011-02-04
I will try that later.. I dont have a usb keyboard ... its a laptop btw

---

### Post by DavidEscott on 2011-03-25
I'm having some issues with my keyboard as well -- my key_release is coming after my subsequent key_press event. So when I type "this" the system is seeing:
KEY_PRESS T
KEY_PRESS H
KEY_RELEASE T
...

The interleaving of the key_press and key_release events seems to confused many applications. In particular firefox's location bar (but not the generic text input widgets) get confused and lose key presses.

I've traced this down to the keyboard/kernel by doing the following:
1. execute `xev > xev.txt` to see the keypresses as X sees them/confirm that X sees interleaved press and release events.
2. a. execute `sudo cat /dev/input/event3 > event.txt` to capture the scan codes seen by the kernel
    b. Utilize the attached make_input.sh and parse.txt (need to rename to parse.c) to make a program to parse the event.txt file (thanks stack-overflow [[http://stackoverflow.com/questions/2547616/how-can-i-translate-linux-keycodes-from-dev-input-event-to-ascii-in-perl]](http://stackoverflow.com/questions/2547616/how-can-i-translate-linux-keycodes-from-dev-input-event-to-ascii-in-perl]))

At the very least this may help you diagnose the source of your difficulties.

 Unfortunately for me the only thing I know to do at this point is type sloooower.

---

### Post by Mosabama on 2011-04-17
wow this is great info even if doesnt help the problem .. thanks alot :)

but I dont think this is the problem as this problem is not always present .. some times the key board works flawlessly.

---

### Post by Mosabama on 2011-04-17
I want to say the problem remains even when the xserver is not running. same thing when I drop to root terminal "recovery mode". so I can say its not X server and its not gnome or anything like that. and its really getting painful

---

### Post by amerinde on 2011-04-17
actually how old is the pc, maybe u just plain wore out the keyboard--- slow down and push harder on the keys

---

### Post by Mosabama on 2011-04-22
it was a BIOS problem from the manufacturer. I updated it and everything is cool now.

Thank you guys for your replies anyway :)

---

