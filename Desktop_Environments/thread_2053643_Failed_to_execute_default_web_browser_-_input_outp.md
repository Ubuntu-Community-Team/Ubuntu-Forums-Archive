---
title: "Failed to execute default web browser - input output error"
date: 2012-09-05
forum: Desktop Environments
---

### Post by unheeding on 2012-09-05
So I have google-chrome-beta (Version 22.0.1229.26 beta) installed, and Xfce is having issues with it.  Whenever I try and pass a URL through to my web browser (say, opening a link from irssi), it opens in a new tab in Chrome (great) but then returns an error saying "failed to execute default web browser - input output error." (profoundly annoying).

This only happens with Chrome, if my browser is set to Opera, it opens in a new tab  in Opera and does not return the error.  Same thing with Firefox.  This bothers me because Chrome is the browser I want to use.  Any ideas on how to resolve this?  Even just suppressing the error message would work wonders for me.  Thanks in advance.

---

### Post by irv on 2012-09-05
> **unheeding said:**
> So I have google-chrome-beta (Version 22.0.1229.26 beta) installed, and Xfce is having issues with it.  Whenever I try and pass a URL through to my web browser (say, opening a link from irssi), it opens in a new tab in Chrome (great) but then returns an error saying "failed to execute default web browser - input output error." (profoundly annoying).

This only happens with Chrome, if my browser is set to Opera, it opens in a new tab  in Opera and does not return the error.  Same thing with Firefox.  This bothers me because Chrome is the browser I want to use.  Any ideas on how to resolve this?  Even just suppressing the error message would work wonders for me.  Thanks in advance.

You are using a beta version and you should expect errors. See if you can file a bug report with Google Chrome. They release beta verison for testing. If you do not want to test it, and want a more solid verison use the latest stable release. If your problem goes away then you will know it is the beta that is the problem.
Just for the record I am having an issue with Chrome but it is different then your problem.

---

### Post by unheeding on 2012-09-05
Okay, the problem was with the Beta/Unstable version of Chrome... although I do really want to run the bleeding edge versions, but obviously they have some problems with Xfce.  (KDE works fine, sigh)

Edit:  Thank you irv.

---

### Post by brihecaton on 2012-10-01
Well, Chrome 22 is the stable version now and I'm having the same problem. Somehow chrome 22 and xfce do things that previously were ok, but aren't anymore

---

### Post by WeNDoR on 2012-10-01
same here ... chrome 22 and xfce do not kiss ...

---

### Post by ccrs8 on 2012-10-01
I am experiencing this as well.  I have Chrome mapped to my "Mail Reader" main menu icon, with gmail and facebook opening up in separate tabs upon launch.  If Chrome is not open already, this works fine.  However, if Chrome is already open, then if I select "Mail Reader" again, a new Chrome window opens and this error occurs.

---

### Post by jigsaw! on 2012-10-01
Did anyone post this error to bugtrack of Chrome or xfce?

---

### Post by johnjaylward on 2012-10-02
> **jigsaw! said:**
> Did anyone post this error to bugtrack of Chrome or xfce?

[https://bugzilla.xfce.org/show_bug.cgi?id=9346](https://bugzilla.xfce.org/show_bug.cgi?id=9346)

---

### Post by unheeding on 2012-10-02
Here's a workaround:

1.  Close Chrome
2.  In Xfce's preferred applications menu, select google-chrome (try changing it to Firefox and back to Chrome if you want to be thorough) 
3.  Start Chrome
4.  When it asks if you want to set it as the default browser, choose no.

and voila, should work.

---

### Post by jonas_t on 2012-10-03
> **unheeding said:**
> Here's a workaround:
[...]
and voila, should work.

Mh, I tried the workaround you're outlining above, but it doesn't work for me. In Google Chrome, I chose not to set it as default browser and it doesn't say so in Chrome's preferences. Nevertheless, the error remains... any ideas? :)

---

### Post by jonas_t on 2012-10-03
It seems exo-open (which is used to launch the default applications) has problems with the return value of Google Chrome.

What works for me, thus, is to have the following shell script set as default "browser", which then redirects each launch request and all parameters to Google Chrome. Most important, it exits with return code 0 and exo-open is happy, no longer throwing the error.

```

#!/bin/bash
/usr/bin/google-chrome $@
exit 0

```

Of course, make sure it's executable by setting chmod correctly, e.g., run "chmod u+x <scriptname>" after saving the script as <scriptname>.

HTH,
Jonas

---

