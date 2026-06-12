---
title: "Making popup notifiers."
date: 2006-08-07
forum: Desktop Environments
---

### Post by yatt on 2006-08-07
[FONT="Verdana"]Is there any app/method to have notifications pop-up and display a message of your choice at a time of your choice?

I want to have reminders to do things like chores and telling my sister to come in. Any ideas?[/FONT]

---

### Post by ardchoille on 2006-08-07
Open a term and run this command:

```

zenity --info --title="This is the title" --text="This is the body text"

```

You can run that from a terminal and it will popup a nice messagebox. You can use that command in a cronjob, but you need something extra:

```

env DISPLAY=:0. zenity --info --title="This is the title" --text="This is the body text"

```

For reasons that I have not yet learned, running the Zenity command from a cronjob will not allow the messagebox to popup unless you tell cron which display to use, that is the "env DISPLAY=:0." part of the above command and it will work in a cronjob.

You can learn more about Zenity with man zenity. Zenity is quite powerful and there are lots of cool things you can do with it.


If you want a small tooltip-like popup near the task tray, you can use this command:

```

/usr/bin/notify-send -u critical -t 30000 -i mail-notification "Title here" "Message body here."

```

But, you need to install libnotify-bin in order to use the notify-send command. You can learn more about notify-send with man notify-send.

---

### Post by Tomosaur on 2006-08-07
Zenity also has a pretty nifty --nofitication option, which will put a notify icon in your taskbar with a message of your choice when the mouse moves across it. It's not as intrusive as the --info option, but you run the risk of not noticing it at all :/

---

### Post by yatt on 2006-08-07
> **ardchoille said:**
> Open a term and run this command:

```

zenity --info --title="This is the title" --text="This is the body text"

```

You can run that from a terminal and it will popup a nice messagebox. You can use that command in a cronjob, but you need something extra:

```

env DISPLAY=:0. zenity --info --title="This is the title" --text="This is the body text"

```

For reasons that I have not yet learned, running the Zenity command from a cronjob will not allow the messagebox to popup unless you tell cron which display to use, that is the "env DISPLAY=:0." part of the above command and it will work in a cronjob.

You can learn more about Zenity with man zenity. Zenity is quite powerful and there are lots of cool things you can do with it.


If you want a small tooltip-like popup near the task tray, you can use this command:

```

/usr/bin/notify-send -u critical -t 30000 -i mail-notification "Title here" "Message body here."

```

But, you need to install libnotify-bin in order to use the notify-send command. You can learn more about notify-send with man notify-send.


Zenity plus cron was just what I was looking for.

---

