---
title: "USPS does not support Ubuntu - what a shame!"
date: 2011-02-24
forum: Desktop Environments
---

### Post by 1script on 2011-02-24
Ubuntu 10.10
Linux HOST 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
Firefox 3.6.13
Adobe Reader 9.4


Trying to print a USPS shipping label. Worked some time before (definitely before 10.10 but may even be before 10.04 on 9.10) Now the Firefox's ***Print*** window never comes up and HTTP Live Header gets overloaded with responses (like 5 in a second) from wsss.usps.com (or some similarly named host at usps.com).

That response appears as a PDF file starting to be served, yet Adobe plugin in Firefox does not respond to that call top action. So, nothing happens and Firefox gets into the never ending cycle. If you leave it like that long enough, becomes non-responsive.

I've re-installed Adobe Reader, not much help.

I don't really like Adobe Reader to be honest, it never zoomed right and for my desktop needs I tend to use Document Viewer instead. So how does one go about replacing Adobe plugin for FF with something that uses Document Reader's facilities, if that's even possible.

Any hint from the community? Thanks!


P.S. Reason to name thread "USPS does not support Ubuntu" was my contact with USPS Live Chat support. The person on the chat was polite but said right off the bat: we don't support anything other than PC and Mac. By PC he meant Windows, of course.

---

### Post by mcduck on 2011-02-25
Just right-click the download link and select "Save Link As" instead of trying to open it directly in your browser.

..and no, you can't use Evince (the default document viewer) embedded inside the web browser. It doesn't have a browser plugin.

---

### Post by 1script on 2011-02-25
Thank you for the tip, mcduck. I honestly had no idea the Document Viewer has an actual name, Evince. It's a great piece of software, in my view much better than Adobe's own Reader.

But, getting back to the issue at hand, on the USPS label printing page there is no link to the label, per se. There is a button that, once you click on it, will use some kind of JavaScript to generate the label, then send it. 

Now that I know the name of the executable file for Evince (/usr/bin/evince , naturally) I've set it up to open PDF documents in FF and will do some more tests as soon as I need another label printed.

---

