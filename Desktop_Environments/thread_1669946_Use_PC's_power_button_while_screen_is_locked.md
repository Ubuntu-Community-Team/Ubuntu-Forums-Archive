---
title: "Use PC's power button while screen is locked"
date: 2011-01-18
forum: Desktop Environments
---

### Post by lukebrannon on 2011-01-18
I am building a small Ubuntu box made for our clients to listen to an audio stream. At startup, I have scripts that start the audio stream, then locks the screen so clients can't change any settings. It works flawlessly.

However, if a client has to shut down the box, they can't. Note this is a headless unit, no monitor, keyboard, or mouse. It will ONLY be used to play streaming audio. I need for the client to be able to safely shutdown the unit by pressing the power button. But, when the power button is pressed, ubuntu asks for the user password. Is there a way to just make the system shutdown without entering a password?

Thanks everyone!

---

### Post by arbitrarychoiceofmoniker on 2011-02-03
Hi,

As root, open the file /etc/acpi/powerbtn.sh

(If anyone reading doesn't know how to do this, you can press Alt+F2 and paste the following command in:

gksudo gedit /etc/acpi/powerbtn.sh)

Now find the line that says:

```
if pidof x $PMS > /dev/null ||
```and add this directly above that line:

```
/sbin/shutdown -h now "Power button pressed"
```now save and exit, press Ctrl+Alt+L to lock your screen - et voila, your machine should unceremoniously shut down when you press the power button.

---

### Post by fmueller01 on 2012-09-21
Sorry, wrong thread.

---

