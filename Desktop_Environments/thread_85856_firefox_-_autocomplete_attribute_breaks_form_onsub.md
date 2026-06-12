---
title: "firefox - autocomplete attribute breaks form onsubmit"
date: 2005-11-03
forum: Desktop Environments
---

### Post by bziman on 2005-11-03
In the latest Breezey version of Firefox, on a page with a form using the (bogus) attribute autocomplete="off", the onsubmit handler is ignored.

Using the following code:
[INDENT][FONT="Courier New"]<form autocomplete="off" name="f1" method="get" onsubmit="alert('1');">
 <input type="submit" name="button" value="1">
</form>[/FONT][/INDENT]

When you click the "1" button, you should get an alert with the message "1" before the submit occurs.  Instead, it simply submits.  If you remove the autocomplete attribute (or change it to a different name, like xautocomplete), the onsubmit happens as expected.  The value of the autocomplete attribute doesn't matter.

I've written a page to demonstrate this at [http://swisspig.net/bug1.html]("http://swisspig.net/bug1.html")

It works fine in Firefox 1.0.7 on Windows and in IE.  Is this a Firefox on Linux issue?  A Firefox on Ubuntu issue?  Anyone seen anything like this before?

For reference, my Firefox is:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.4 (Ubuntu package 1.0.7)

Thanks,
Brian

---

