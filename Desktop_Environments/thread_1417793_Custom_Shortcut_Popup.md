---
title: "Custom Shortcut Popup"
date: 2010-02-27
forum: Desktop Environments
---

### Post by skooter1121 on 2010-02-27
I'm trying to have a customized list of shortcuts available at the desktop.

For example; I've got custom commands to help enter text, apply special styles, dictionary lookups in Open Office. I keep forgetting what some of them are.

I'm looking for something like notify-send. I like the way it looks, but I can only show a few lines of text. Can it be enlarged?

I have looked at zenity, xmessage, gmessage, and notify-send but nothing looks as nice.

Any suggestions?

---

### Post by Zorael on 2010-02-27
(There's kdialog, too.)

```
$ kdialog --title "Hey, listen\!" --passivepopup "1<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>9<br>10<br>11<br>12<br>13<br>14<br>15<br>16<br>17<br>18<br>19<br>20<br>21<br>22<br>23<br>24<br>25<br>26<br>27<br>28<br>29<br>30" 5
```

---

### Post by skooter1121 on 2010-02-27
I think I choose the wrong OS, as I'm running Gnome, Is there a version for Gnome?


Thank you.

---

