---
title: "Installed game patch.."
date: 2006-01-11
forum: Gaming &amp; Leisure
---

### Post by Sordo on 2006-01-11
I just got installed tribes 2 update, but when i started the game, i noticed that sounds was gone.

What could be the problem?
Before the patch sounds was fine...

---

### Post by Perfect Storm on 2006-01-11
Can you get some terminal output on it for errors? (run the game in the terminal)

---

### Post by Sordo on 2006-01-11
[QUOTE=Artificial Intelligence]Can you get some terminal output on it for errors? (run the game in the terminal)[/QUOTE]
BUG! (Segmentation Fault)  Going down hard...
Tribes 2 for Linux #25026
Built with glibc-2.1 on x86
Stack dump:
{
        0xffffe420
        0x81d9834
        0x81d1bf3
        0x823d038
        0x81d7457
        0xb7cdbea2
        0x8050b41
}
Please send a full bug report,
along with the contents of autosave to: [email]support@lokigames.com[/email]
Unable to execute loki_qagent - exiting


Gives that kind of error message, when running on console

---

### Post by akurashy on 2006-01-11
Have you googled the error? maybe it can help a bit

---

### Post by Sordo on 2006-01-11
WOohooo, 
found an answer from linuxquestions.org.
Thanks anyway.

Basicly all I had to do was go to home directory and remove file from .loki/tribes2/base/prefs called ClientPrefs.cs

When tried to go cd tribes2 it said that permission denied in all dirs.
Then just had to sudo chmod directories one by one.

---

