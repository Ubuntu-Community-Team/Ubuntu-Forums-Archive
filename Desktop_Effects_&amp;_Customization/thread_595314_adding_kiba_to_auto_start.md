---
title: "adding kiba to auto start?"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by thousandpimps on 2007-10-28
jus a simple question..how do i add my kiba dock to start when i turn on my computer

---

### Post by Forlong on 2007-10-28
Assuming you're on GNOME:

System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs &#8594; Add

---

### Post by thousandpimps on 2007-10-29
i got there but i dont know what to select from the kiba dock folder...since its not like windows and they are exe files

---

### Post by Mr Greencastle on 2007-10-29
He didn't finish;

System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs &#8594; Add

Name: Kiba Dock
Command: kiba-dock

Hope that helped!

Mr Green

---

### Post by Lista on 2007-11-11
I'd like to use this thread for a 'problem' I'm experiencing.
Installing itself went without troubles, and I can start Kiba from Terminal. However, when I exit Terminal, I exit Kiba too. One question here; can I run Kiba from Terminal like a 'background' process, so that when I exit Terminal, I do not shut down Kiba too?

I've added kiba-dock to the list of the programs that are supposed to run on start-up, and it in fact does (because I see it in the running programs tab), but the dock isn't visible, even though it appears to be running.

Can anyone help me with this?

---

### Post by Seisen on 2007-11-11
If you go to the Applications>Accessories Menu Kiba-Dock should be listed there to so that way you don't have start kiba-dock from the terminal.

---

### Post by Forlong on 2007-11-11
And you can always use [Alt]+[F2] of course.

Don't know about the startup issue, though. Hopefully someone that actually uses Kiba comes along to help out. :)

---

### Post by Lista on 2007-11-11
Thank you guys for your answers.

Running it from the Applications menu did solve the problem (at least temporarily), but I really wanted it to start automatically. And even though the 'manual' addition to the list of programs to be started didn't work, this did:

[http://www.kiba-dock.org/index.php?option=com_content&task=view&id=16&Itemid=25](http://www.kiba-dock.org/index.php?option=com_content&task=view&id=16&Itemid=25)

It's a FAQ entry from the official site, describing how to copy and paste kiba-dock.desktop file that already exist to your autostart directory. It solved my autostart related problems 100%!

---

