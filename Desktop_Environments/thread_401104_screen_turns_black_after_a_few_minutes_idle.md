---
title: "screen turns black after a few minutes idle"
date: 2007-04-04
forum: Desktop Environments
---

### Post by ilanesh on 2007-04-04
I have a very bad problem with ubuntu, always when a few minutes Idle the screen turns black and I have disabled it but it  don`t helps at all. I want that my screen on ubuntu always stays open, how to do this? with all tryings i could not find out how to stop this, it drives me crazy.
Also the screensaver i can only make it that it is after two houres idel, i want to disable everything that my screen stays just normal also when i am not on the computer, i have the proble with both, also laptop and alsp desktop.
Why by all means is there anything to do about this?
Heeeeeeeeeeelp!!!!

---

### Post by ilanesh on 2007-04-04
any Ideas???

---

### Post by ilanesh on 2007-04-05
well well well, here in this forum is no help at all! Grumble!:mad: 
For what is this forum here?
Onnly for the beauty?
Why noone gives and answer here? Huh???
What should that be??? :mad: :mad: :mad: :mad: :mad: :mad:

---

### Post by ilanesh on 2007-04-05
Cheez, can here at least someone tell me what to do?
 HEEEEEEEEEEEEEEEELP!!!!!!!!!!!!!!!!!!!!!!!!!!1:confused:

---

### Post by ilanesh on 2007-04-06
??????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????

---

### Post by siefer132 on 2007-04-06
Try going into the Screensaver section, and pressing the power management button. Should help:).

---

### Post by FoundmyTux on 2007-04-06
Go to System Preferences Power Management 
Slide the button below Put display to sleep when computer is inactive for completely to the right until it says never.

Now go to system preferences Screensaver and uncheck the box infront of Activate screensaver when session is idea.

---

### Post by foug on 2007-04-16
i've been having this problem too. I've down everything both you have said but it still goes idle.

---

### Post by jocko on 2007-04-16
One thing that causes a problem that fits your description is if you run Xgl as a separate session.
In that case you can fix it by:
```
sudo gedit /etc/X11/xorg.conf
```
And add these lines:
```
Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection
```
Restart Xorg by Ctrl+Alt+Backspace.
Even if you don't use Xgl I guess this could solve your problem, so try it out.
If it doesn't help you'll probably have to give more information about your computers.

---

### Post by soapergem on 2007-04-25
I tried all those suggestions as well, but to no avail. What did work, though, was running this in the terminal:

```
killall gnome-screensaver
```

That works for the current session, and I found from another forum post that this will prevent the screensaver from starting up at all:

```
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false
```

---

