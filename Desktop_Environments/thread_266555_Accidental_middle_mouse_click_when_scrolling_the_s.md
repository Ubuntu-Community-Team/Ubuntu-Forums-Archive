---
title: "Accidental middle mouse click when scrolling the scroll wheel"
date: 2006-09-27
forum: Desktop Environments
---

### Post by sfp-a7x on 2006-09-27
Frequently, when I'm spinning the scroll wheel on my mouse really fast, I'll get a middle click event.  This is particularly annoying when editing text because I will paste a block of text and then I'll scroll right by without ever seeing the unwelcome text.

Is there a way to tell X to ignore middle clicks if the scroll wheel is used immediately before or after the click?  For example, it would be cool if X did the following upon receiving a middle click:

[LIST]
[*]was the scroll wheel used within the last 200ms?  if so:
[LIST]
[*]ignore the middle click
[/LIST]
[*]otherwise:
[LIST]
[*]wait 100ms
[*]was the scroll wheel used within the last 100ms?  if so:
[LIST]
[*]ignore the middle click
[/LIST]
[*]otherwise:
[LIST]
[*]process the middle click
[/LIST]
[/LIST]
[/LIST]

Any suggestions?

Thanks!

---

