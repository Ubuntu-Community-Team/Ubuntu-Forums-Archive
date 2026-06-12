---
title: "Error: Object Expect"
date: 2007-04-17
forum: Forum Feedback &amp; Help
---

### Post by DeadEyes on 2007-04-17
Running IE6, I keep getting Error:Object Expected every time a page loads.
The debugger points to this line:
```

$('q').addEvent('focus', function() {
    $('q').select();
});

```
Its begining to get really annoying, It does not seem to happen with firefox but in work I don't have the option.

---

### Post by thelinuxguy on 2007-04-17
Do you get a dialog box showing that error? You can turn off the dialog box by unchecking the option which goes like "Display a message about every script error" under Internet options >> advanced.

I am on Ubuntu and Firefox right now. Will edit this thread with the exact location of that option when I get to Win + IE. And besides, Firefox just doesn't pop up a dialog. You can still see the error by pulling down the Error Console from Tools menu.

Edit: 
IE 6 : Tools >> Internet options >> Advanced 
Uncheck "Display a notification about every script error"

Does this help?

---

### Post by ubuntu-geek on 2007-04-17
Should be fixed now. Please let me know if it isnt.

---

### Post by thelinuxguy on 2007-04-17
Firefox error console doesn't show it now.

---

### Post by DeadEyes on 2007-04-18
The change does not appear to have had any effect. It could just be my setup. I'm sure, I'm not the only person who views the forum using Win+IE6 yet no one else seems to be bothered by it, or at least not enough to point it out.

> **thelinuxguy said:**
> IE 6 : Tools >> Internet options >> Advanced 
Uncheck "Display a notification about every script error"

Does this help?

Thanks for that thelinuxguy however I need to keep it on for work.

---

### Post by silurius on 2007-10-03
I get this in IE 7.0.5730.11 (with no dialog box)

> Char:    3
Error:   Object expected
Code:    0
URL:     [http://ubuntuforums.org/](http://ubuntuforums.org/)

Which points to the same line of code as in the OP:

```
		$('q').addEvent('focus', function() {
```

Perhaps there needs to be an additional IF statement for IE7?

---

