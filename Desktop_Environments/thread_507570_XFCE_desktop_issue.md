---
title: "XFCE desktop issue"
date: 2007-07-23
forum: Desktop Environments
---

### Post by ondpanda on 2007-07-23
Well thats what i think it might be. I recently installed the latest stable  Xubuntu and it worked like a charm. However now my top and bottom bars (including the launch, shutdown and mutliple desktop icons) are gone. Furthermorer i cant launch programs such as spredshee with the right-click menu, that is i can launch 'em and by using alt-tab i can see they are running, but icant use or see them. Please help as i'm quite new at this.

---

### Post by DJiNN on 2007-07-23
Can you right click & get access to the "Settings" menu? If so, "Right Click" & choose "Desktop Settings". Tick the box that says "Allow XFCE to manage the Desktop" if it's not already ticked.  I'm guessing that could be the problem. Let me know how it goes? :)

DJiNN

---

### Post by ondpanda on 2007-07-23
doesn't work. I can start a failsafe terminal, but that't about it. THX btw:)

---

### Post by Gruelius on 2007-07-23
maybe just reisntall xubuntu-desktop and go from there. Sounds like you may have changed a config (on purpose or accidentally).

sudo apt-get install xubuntu-desktop

---

### Post by ondpanda on 2007-07-23
will this affect my stored data (i.e. documents, music etc.?)

---

### Post by ondpanda on 2007-07-23
Got the desktop preferences to work (actually i just tried again) and xfce is managing my desktop. The remaining programs mysterouisly also work again, still i would really like the top and bottom bars back... BTW the reinstall command above does not work.

---

### Post by crimesaucer on 2007-07-23
When your top and bottom panels disappear and you can't right click them, then do this:

do "alt+f2" to run a command.

type this command in "alt+f2" and press enter:

```
xfce-panel &
```

---

### Post by ondpanda on 2007-07-23
@crimesaucer

the given command "xfce-panel" does appearently not exist... :(

---

### Post by crimesaucer on 2007-07-23
> **ondpanda said:**
> @crimesaucer

the given command "xfce-panel" does appearently not exist... :(


Did you run it in alt+f2, or Terminal?


Do it in alt+f2:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-59-3.png[/IMG]


You might also have to start with the command:

```
killall xfce-panel
```

then:

```
xfce-panel &
```

---

### Post by ugm6hr on 2007-07-23
> **ondpanda said:**
> @crimesaucer

the given command "xfce-panel" does appearently not exist... :(

As crimesaucer's repeat post states - it's:

```
xfce[COLOR="Red"]4[/COLOR]-panel &
```

---

### Post by crimesaucer on 2007-07-23
> **ugm6hr said:**
> As crimesaucer's repeat post states - it's:

```
xfce[COLOR="Red"]4[/COLOR]-panel &
```


Oopps...I am so sorry that I didn't see that I left the 4 off of the code.


My bad. Thanks ugm6hr for noticing I had written a typo.


So that would also be:

```
killall xfce4-panel
```

---

### Post by ondpanda on 2007-07-24
Thank you very much! this (the xfce4 command thing) does work, however i want it to be like that at logon, instead  of me having to enter t every time. Any clues?

---

### Post by ugm6hr on 2007-07-24
Have you tried turning off with the "Save session for future logins" box ticked (in the panel that appears when you click the Quit panel icon)?

If that doesn't work, the other option is to add "xfce4-panel" to the Autostarted Applications (Applications->Settings).  I have seen that used as a solution by others in this forum.

---

### Post by ondpanda on 2007-07-24
Thx a bunch for all your help :)

---

### Post by crimesaucer on 2007-07-24
> **ondpanda said:**
> Thank you very much! this (the xfce4 command thing) does work, however i want it to be like that at logon, instead  of me having to enter t every time. Any clues?

If you put the "&" sign at the end of the command, it should show up permanently.

```
xfce4-panel &
```

---

