---
title: "How can I get indicators for running applications?"
date: 2012-06-12
forum: Desktop Environments
---

### Post by bobdobbs on 2012-06-12
Hi.
I've recently started using KDE after upgrading to ubuntu 12.04.
I used to use gnome, and I'm quiet used to it's features. (But after y upgrade, gnome become unusable for my requirements)

One thing that gnome had that I liked was a feature in it's panel that would give indicators for some currently running apps. Like, if skype was running, you could see your status, and you could see alerts for recent messages. If I clicked the skype icon, I could restore skype.

Under KDE, if I hit the close icon for skype, skype remains running in the background, but there is no way to recover the window. I have to kill the process and restart it.

Not even alt-tab will restore it.

Also, there is no indicator for media players. I like running banshee, but the same problem with skype exists with banshee: closing it makes the GUI irrecoverable, even though the process still runs.


Is there a way to emulate the functioning gnome behaviour on KDE? Otherwise, is there a third-part application that will give me a dock that will show activity for skype, banshee, other applications or connected devices?

I've used docky before, but it also has a similair problem with skype: if you close skype, then the GUI become "lost" while the process still runs, and clicking the skype icon just opens another instance of skype.

---

### Post by carl4926 on 2012-06-13
Sounds like you are missing a system tray widget on the kde panel
Or
What about hidden icons

---

### Post by bobdobbs on 2012-06-13
> **carl4926 said:**
> Sounds like you are missing a system tray widget on the kde panel
Or
What about hidden icons

How do I install a system tray widget?

What do you mean about hidden icons?

---

### Post by bobdobbs on 2012-06-13
> **bobdobbs said:**
> How do I install a system tray widget?

What do you mean about hidden icons?

Ah, ok.

I figured out how to install a system tray widget.

Problem is, it doesn't help with skype. Minimizing skype still makes the GUI irrecoverable. When it's running, there's no access to the GUI, or any activity indication in the system tray.

---

### Post by carl4926 on 2012-06-13
I don't use skype. Check in skype setting to see if there is a setting related to the system tray notification area
Also make sure you actually have a task manager widget, which will mean, when you have a application window open, it will be seen in the panel

---

### Post by carl4926 on 2012-06-13
Hidden icons are accessed via the small triangle in the tray. You can change the settings for this too.

---

### Post by bobdobbs on 2012-06-13
> **carl4926 said:**
> I don't use skype. Check in skype setting to see if there is a setting related to the system tray notification area
Also make sure you actually have a task manager widget, which will mean, when you have a application window open, it will be seen in the panel

Well, that's the problem: if the application is running but the main window is closed, the entire application is not available at all, until I kill the process or restart it.

---

### Post by carl4926 on 2012-06-13
What if you minimise the window, is it visible in the panel?

---

### Post by bobdobbs on 2012-06-13
> **carl4926 said:**
> Hidden icons are accessed via the small triangle in the tray. You can change the settings for this too.

I see the triangle, but it doesn't list skype or banshee.

It lists some things called "akonadi", "desktop search file indexing" and devices.

But it doesn't list any running applications.

Is there a way to customize the system tray so that it lists my running applications? Or otherwise lets me access them?

I've also noticed that alt-tab wont show any minimized applications at all.

---

### Post by bobdobbs on 2012-06-13
> **carl4926 said:**
> What if you minimise the window, is it visible in the panel?

No.

---

### Post by carl4926 on 2012-06-13
You need to add a task manager widget

Did you remove the default panel or something?

---

### Post by bobdobbs on 2012-06-13
> **carl4926 said:**
> You need to add a task manager widget

Did you remove the default panel or something?

No, I haven't removed any panels.

I've installed the task managet widget. It does show some applications, but not others.

Again, the problem is skype. If skype is minimized, the task manager widget doesn't show it, and I have to find and kill the process.

---

### Post by carl4926 on 2012-06-13
Like I said. Check in the skype application settings for any config related to the tray

---

### Post by bobdobbs on 2012-06-13
> **carl4926 said:**
> Like I said. Check in the skype application settings for any config related to the tray

The only setting I can find in skype that touches on this is a single checkbox: "start skype minimised in the system tray".

This isn't what I want, but I checked it anyway and restarted skype.

After restarting skype, the problem persists.

---

### Post by carl4926 on 2012-06-13
Is skype listed in the applications for hiding / unhiding ?

---

### Post by bobdobbs on 2012-06-13
> **carl4926 said:**
> Is skype listed in the applications for hiding / unhiding ?

How do I access this list?

---

### Post by carl4926 on 2012-06-13
Right click the small triangle for the hidden icons

Also, you might want to try this:
Create a new test user
Login with it and see if it has the same problems. Report back

---

