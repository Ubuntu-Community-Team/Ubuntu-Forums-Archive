---
title: "power button not working"
date: 2011-10-18
forum: Desktop Environments
---

### Post by tismij on 2011-10-18
just finished installing xubuntu 11.10 and everything works like a charm,  except the power button.
Somehow xubuntu does not respond to me pressing the powerbutton.

I set the action to shutdown in power settings, I tested with xev and it "sees" me pressing the power button, just nothing is happening when i press it.

I can shutdown fine from the menu but would really like to just shutdown by pressing the button, it is the only little annoyance with my otherwise excellent xubuntu experience so far.

Any ideas?

---

### Post by Linuxratty on 2011-10-18
> **tismij said:**
> .

I can shutdown fine from the menu but would really like to just shutdown by pressing the button, it is the only little annoyance with my otherwise excellent xubuntu experience so far.

Any ideas?
 I've read this elsewhere about Xubuntu. I've also read that it's better for your computer and the OS to shutdown using the GUI rather than just whacking the power button. If you just hit the power button,this does not give the OS a chance to save everything properly for next time.

---

### Post by Toz on 2011-10-18
> **tismij said:**
> just finished installing xubuntu 11.10 and everything works like a charm,  except the power button.
Somehow xubuntu does not respond to me pressing the powerbutton.

I set the action to shutdown in power settings, I tested with xev and it "sees" me pressing the power button, just nothing is happening when i press it.

I can shutdown fine from the menu but would really like to just shutdown by pressing the button, it is the only little annoyance with my otherwise excellent xubuntu experience so far.

Any ideas?

If you go to Settings Manager -> Power Manager, there is an option there to select an action "When power button is pressed". What is it currently set to?

EDIT: An oh, by the way, welcome to the forums (just noticed it was your first post).

---

### Post by tismij on 2011-10-19
> **Toz said:**
> If you go to Settings Manager -> Power Manager, there is an option there to select an action "When power button is pressed". What is it currently set to?

EDIT: An oh, by the way, welcome to the forums (just noticed it was your first post).


Thanks.
Currently it is set to shutdown but I have also tried "ask" and neither works.
Button works xubuntu is just not performing the set action.

As for the previous message, I have a laptop and usually press power shortly to get ubuntu to shutdown nicely not simply cut off its power by keeping the power button pressed till my laptop is off :)

---

### Post by Toz on 2011-10-19
Interesting. I have a fresh install of 11.10, with the setting set to Ask, and when I press the power button it pops up the logout dialog.

Try running "acpi_listen" in a terminal window and pressing the power button. What response do you get? I get:
> button/power PWRF 00000080 00000004

(/etc/acpi/events/powerbtn handles this event and calls the script /etc/acpi/powerbtn.sh)

What is the make/model of your laptop? 
Do you have acpid installed?

---

### Post by tismij on 2011-10-19
> **Toz said:**
> Interesting. I have a fresh install of 11.10, with the setting set to Ask, and when I press the power button it pops up the logout dialog.

Try running "acpi_listen" in a terminal window and pressing the power button. What response do you get? I get:


(/etc/acpi/events/powerbtn handles this event and calls the script /etc/acpi/powerbtn.sh)

What is the make/model of your laptop? 
Do you have acpid installed?

acpi_list shows: button/power PWRF 00000080 00000001

(00000001 changes to 00000002 etc. after each press of the powerbutton as it should)

/etc/acpi/events/powerbtn
event=button[ /]power
action=/etc/acpi/powerbtn.sh

Laptop is a Dell Vostro 3750

--- one step further
If I change the action in events/powerbtn to action=/sbin/shutdown -h now it works fine.
Seems the problem is in powerbtn.sh somewhere, I'm guessing it has something to do with the power manager in xubuntu (the script checks for powermanagers and lets them take over if they are present).

I prefer to use the script so any tips on checking the powermanager and fixing this ?

---

### Post by Toz on 2011-10-19
Are there any messages in ~/.xsession-errors regarding xfce4-power-manager or when you press the power button?

Also, what is the contents of your ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-power-manager.xml file? Mine is:
```
<?xml version="1.0" encoding="UTF-8"?>

<channel name="xfce4-power-manager" version="1.0">
  <property name="xfce4-power-manager" type="empty">
    <property name="power-button-action" type="empty"/>
    <property name="hibernate-button-action" type="uint" value="2"/>
    <property name="sleep-button-action" type="uint" value="1"/>
    <property name="lid-action-on-ac" type="uint" value="1"/>
    <property name="critical-power-action" type="uint" value="3"/>
    <property name="lid-action-on-battery" type="uint" value="1"/>
  </property>
</channel>

```

You could also kill xfce4-power-manager and restart it with:
```
xfce4-power-manager --no-daemon
```
...for debugging.

EDIT: Here is a related link at the xfce forums: [http://forum.xfce.org/viewtopic.php?id=6158]("http://forum.xfce.org/viewtopic.php?id=6158")

---

### Post by tismij on 2011-10-19
> **Toz said:**
> Are there any messages in ~/.xsession-errors regarding xfce4-power-manager or when you press the power button?

Also, what is the contents of your ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-power-manager.xml file? Mine is:
```
<?xml version="1.0" encoding="UTF-8"?>

<channel name="xfce4-power-manager" version="1.0">
  <property name="xfce4-power-manager" type="empty">
    <property name="power-button-action" type="empty"/>
    <property name="hibernate-button-action" type="uint" value="2"/>
    <property name="sleep-button-action" type="uint" value="1"/>
    <property name="lid-action-on-ac" type="uint" value="1"/>
    <property name="critical-power-action" type="uint" value="3"/>
    <property name="lid-action-on-battery" type="uint" value="1"/>
  </property>
</channel>

```

You could also kill xfce4-power-manager and restart it with:
```
xfce4-power-manager --no-daemon
```
...for debugging.

EDIT: Here is a related link at the xfce forums: [http://forum.xfce.org/viewtopic.php?id=6158]("http://forum.xfce.org/viewtopic.php?id=6158")

well it is exactly my problem described in the provided topic, just no easy and neat solution.
Seems the best way really is changing the action in powerbtn from running the script to a shutdown command.
Question now is exactly which command gives the best clean shutdown method, simply shutdown -h now shuts it down but not sure if it is a clean shutdown or a hard power off.

Anyone know the proper command to give a nice and proper shutdown of my laptop?

btw, the rest seems to work fine, never use suspend so not sure but power management does work.

P.S. the power off button works fine if I use it before I login but after login it is a no go.

---

### Post by Toz on 2011-10-19
Well, the proper command to run would be **xfce4-session-logout --halt** because according to "man xfce4-session-logout", it will save the session before shutdown. The only problem is that when run from /etc/acpi/events/powerbtn, it is run as root, and as such, it won't have access to your xfce session to properly save the session. If you look at the previous link, the last post by paolo321 has a solution whereby the shutdown (in that case logout) is done properly by identifying and using the active user session.

---

