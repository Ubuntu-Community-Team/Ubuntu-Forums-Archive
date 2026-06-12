---
title: "unity system tray with dual monitors"
date: 2012-05-04
forum: Desktop Environments
---

### Post by chtdt on 2012-05-04
I have a Java application that places an icon in the unity system tray.   

It shows up fine when I'm on a single monitor.    When I have my laptop plugged into another monitor, there are two system trays: one for each screen.

The list of icons in the system tray are the same - except for my application's icon.    It only shows up on my laptop's system tray, and not on my main monitor system tray.

In Java, I get a handle to the system tray via:
        final SystemTray tray = SystemTray.getSystemTray();

I don't see an way to get the "other" system tray, if there really is one.

How would I go about getting my icon onto both, or alternatively, is there a way to only have the system tray on my main monitor?

---

### Post by wowone on 2012-05-12
The same problem. It happened after updating to Ubuntu 12.04. On the previous version it worked correctly.

---

### Post by tomrichy on 2012-05-12
I have the same problem with the Skype icon.

---

### Post by Redonk on 2012-06-13
I too would like to know how to have one system tray or "unity bar" on my main monitor. When passing from one monitor to the second the cursor hangs on the bar. This is very frustrating as I have to whip the mouse quite fast just to overcome the hang from the bar.

---

### Post by *Legion* on 2012-08-29
This is my **biggest** complaint with Unity right now. Is there really no resolution to the problem?

I'd either want to have the notification area/system tray appear on my main monitor only, or at the very least be completely duplicated across all monitors.

Right now, the Unity icons are duplicated but the whitelisted icons do not.

At bare minimum, I'd like a way to have the one tray that has all icons appear on my main monitor! It's hell having it off on a side monitor.

> **Redonk said:**
> I too would like to know how to have one system tray or "unity bar" on my main monitor. When passing from one monitor to the second the cursor hangs on the bar. This is very frustrating as I have to whip the mouse quite fast just to overcome the hang from the bar.

What you're describing is the "sticky edges" behavior. Go to Displays and set Sticky Edges to Off.

---

### Post by FreedomOverdose on 2012-10-03
I have this problem too! Has it been reported somewhere? It's really annoying! :(

---

