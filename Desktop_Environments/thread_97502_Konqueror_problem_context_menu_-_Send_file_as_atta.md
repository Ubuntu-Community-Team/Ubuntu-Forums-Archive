---
title: "Konqueror problem: context menu - Send file as attachment using Thunderbird"
date: 2005-12-01
forum: Desktop Environments
---

### Post by realman on 2005-12-01
Hi,

I'm trying to create new Konqueror context action "Send file as attachment" and force Thunderbird to do it.

According to [http://www.mozilla.org/docs/command-line-args.html](http://www.mozilla.org/docs/command-line-args.html), there is approtiate command:
```
mozilla-thunderbird -compose "attachment:file:///home/realman/somefile"
```
but it doesn't work!
It opens new mail window, but no attachment is set.

Doesn't works even "simple" command like this:
```
mozilla-thunderbird -compose "to=someone@domain.com"
```
This command should open new mail window with recipient adress "someone@domain.com" filled already, but every fields are empty.

Do you have any ideas how to force Thunderbird to cooperate?

I use Kubuntu 5.10 and Mozilla-Thunderbird 1.0.7.


Pawel Gradziel,
jabber: pgradziel//jabber.ebox.pl

---

### Post by realman on 2005-12-01
Found out, that it is a Thunderbird bug:
[https://bugzilla.mozilla.org/show_bug.cgi?id=316177](https://bugzilla.mozilla.org/show_bug.cgi?id=316177)

---

