---
title: "Changing Date and Time"
date: 2005-07-28
forum: Desktop Environments
---

### Post by elder68 on 2005-07-28
When I want to change the date or the time, I right-click on the clock and select "Change Date or Time." This then asks for my password, which I enter, and then nothing happens. Nothing comes up. 

Can anyone help with this please.

Bill.

---

### Post by Xian on 2005-07-28
Try to get the window to open by using the terminal.
Enter this text into Konsole (or similar):

```
$ sudo /usr/bin/kcmshell kde-clock.desktop
```

---

### Post by elder68 on 2005-07-29
[QUOTE=Xian]Try to get the window to open by using the terminal.
Enter this text into Konsole (or similar):

```
$ sudo /usr/bin/kcmshell kde-clock.desktop
```[/QUOTE]

Thanks for this, it worked.

---

### Post by sprucio on 2005-07-31
Is this a KDE bug or a Kubuntu bug?

---

### Post by ericm_06 on 2005-08-02
I believe it is related to the Administrator Mode bug in KDE 3.4.0 and 3.4.1

---

### Post by elder68 on 2005-08-02
[QUOTE=ericm_06]I believe it is related to the Administrator Mode bug in KDE 3.4.0 and 3.4.1[/QUOTE]

It must be as I was able to make the change via the terminal suggestion I got earlier it still acted buggy.

The date changed fine but the time acts oddly. You set the time, click "apply" the screen goes black, then it comes back. When it comes back, the time on the clock is different to what I set, but the time on the screen is OK.

Oh welll....

Cheers...

---

