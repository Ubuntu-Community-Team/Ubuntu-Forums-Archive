---
title: "(Very) odd bug in compiz"
date: 2008-01-14
forum: Desktop Effects &amp; Customization
---

### Post by sammydee on 2008-01-14
Hi all

Now I'm fairly sure (but not certain) that this bug is due to compiz because it never seems to happen when compiz is disabled.

At seemingly random intervals at a frequency of about once a week, X will lock up and will not accept any keyboard input. It acts exactly as if the ctrl key was being continuosly held down and no other keystrokes registered. this means that I can't click the off button in ubuntu (try it with the ctrl key held down) so I have to do a hard kill of the power. This has happened over at least two reinstalls of ubuntu. The laptop is a HP dv6000 with an nvidia 7400. Has anybody else ever experienced this rather bizarre error?

Sam

---

### Post by rune0077 on 2008-01-14
Weird. Never experienced this. Since ctrl+alt+backspace logs you out of a session, and if your ctrl is being constantly pressed, maybe you could just press alt+backspace to log out. Doesn't fix your problem, but at least it'll save you from hitting the power switch each time.

---

### Post by chrisccoulson on 2008-01-14
If I click the logout button with my CTRL key pressed, the exit window appears as normal, so I don't think your machine is behaving as if the CTRL key is pressed. Maybe Compiz is just locking up?

Are you sure ctrl+alt+backspace doesn't kill the server. Does ctrl+alt+f1 get you to a terminal?

---

### Post by mickey57 on 2008-01-14
[COLOR="DarkRed"][SIZE="3"].....Same problem here.I have disabled compiz because of a dimming issue.The keyboard still doesn't respond sometimes.I am using a usb keyboard and mouse combo from Kensington..I am thinking it is a usb issue now.:confused:[/SIZE][/COLOR]

---

### Post by sammydee on 2008-01-15
No other keys do ANYTHING at all, so any ctrl-alt-combo does nothing. I can switch between applications using compiz's expose feature, but the panel and panel buttons are unresponsive. If I click on items on the desktop, multiple items are selected EXACTLY as if the ctrl key is being held down. Text highlighting with the mouse behaves in the same way.

---

### Post by sammydee on 2008-01-22
I switched to the latest nvidia drivers (169.07) and *cross fingers* the bug SEEMS to have disapeared - IE I haven't had it for about a week. Let's hope it stays that way...

Sam

---

