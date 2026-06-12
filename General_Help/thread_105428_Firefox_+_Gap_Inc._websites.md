---
title: "Firefox + Gap Inc. websites"
date: 2005-12-18
forum: General Help
---

### Post by Casey on 2005-12-18
When visiting:
[http://www.gap.com]("http://www.gap.com")
[http://www.bananarepublic.com]("http://www.bananarepublic.com")
[http://www.oldnavy.com]("http://www.oldnavy.com")

**my wife recieves this error message:**

We're sorry, but we do not support the version of the browser you are using.
Our site works best with the following browsers:

PC users
Internet Explorer 5.5 and above Download browser
Netscape 7 and above Download browser
Mozilla (including Firefox) 1.0 and above Download browser

Mac users
Netscape 7 and above Download browser
Mozilla (including Firefox) 1.0 and above Download browser

We're working on supporting Safari. Please check back soon.

--------

It doesn't appear that they support firefox on linux, but she emailed them and the first response was a form letter saying that they don't support linux.  She did however, email back for more information as to the reason, and they assured her that they did, in fact, support linux (apparently they contacted the IT department to discover this), and that they would forward her comments on to the IT department.

Since then, nothing has changed, though it now appears that her browser is being recognized as safari??  Does anyone else running ubuntu have this problem?

This is under firefox 1.5, but also exists under the 1.07 version which comes with ubuntu.

If they really don't support linux, she doesn't want to order from them, but if this is just an issue with her install, she would like to know how to correct it.

Thanks for any help,
-- Casey

---

### Post by Casey on 2005-12-18
I have just confirmed that it still does not work under the version of 1.07 that ships with ubuntu.

---

### Post by jrib on 2005-12-18
Look for the User Agent Switcher extension for firefox (here is the homepage: [http://chrispederick.com/work/useragentswitcher/](http://chrispederick.com/work/useragentswitcher/) ).  Then you can tell whatever you want about which browser you use.  Probably just an unintentional javascript since they support firefox for windows....

[e]I just tried it by setting my User Agent to "Netscape 4.8 (XP)", which is one of the presets, and all of those sites work fine.  Happy shopping :)

---

### Post by Casey on 2005-12-18
If that's the case, then we'd rather not buy things from there.  If they won't support linux users, there's no reason that we should support their business.

Edit: My wife would like me to mention that this once did work.  It is only recently that they have changed their site to prevent certain browsers from using it.

---

### Post by kaamos on 2005-12-18
Just checked, works with useragent switcher. Get it here [https://addons.mozilla.org/extensions/moreinfo.php?id=59](https://addons.mozilla.org/extensions/moreinfo.php?id=59)

Damn poorly done websites..

---

### Post by Ibbelz on 2005-12-18
Yes, user agent switcher is a nice extension for this kind of problems. Just fake that you're IE or something. Everything will work nicely then, haha. :)

---

### Post by jrib on 2005-12-18
I'm sending them an email too

---

### Post by Casey on 2005-12-18
I have sent them an email, so that further ubuntu/linux users will not have this problem.  It would be appreciated if more people would help out (contributing UA strings to them and such) by emailing.  The email message (obtained from [www.gapinc.com](www.gapinc.com) is [EMAIL="custserv@gap.com"]custserv@gap.com[/EMAIL].  Here's the text of my message, if you'd like somewhere to start:


I'm using firefox and the gap.com website still will not allow access.  A bit of research has shown that this is because the part which disallows access is poorly coded (as it apparently relies heavily on the user agent strings being identical as they often are in Windows).  In any case, this is my user agent string, which your site does not allow:
"Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8 ) Gecko/20051111 Firefox/1.5"

If you could forward this to the IT department that would be great.

A bit of research shows that UA spoofing would allow the site to work.  When you forward this message, please let your IT department know that more discussion is available here:
[http://www.ubuntuforums.org/showthread.php?t=105428](http://www.ubuntuforums.org/showthread.php?t=105428)

Thank you for your help,
Casey

---

### Post by briancurtin on 2005-12-18
i actually noticed this same thing 2 weeks ago when a friend tried to show me some things from Old Navy that she wanted. she uses firefox on XP, i used it on FC4 at the time, and i knew it had to be something stupid rejecting me.

---

### Post by DoddyUK on 2005-12-18
It's the same problem with Opera 8.51 on Ubuntu Breezy, though I'm not certain if the same is true or not under Windows.

---

### Post by briguy on 2005-12-18
Fired one off too.

---

### Post by viscount on 2005-12-18
What email address are you guys sending these "please stop being dorks and let
linux users have access to your sites" letter?

I would like to send one off too, so would my wife.
We should try to send them all to the same place, more of an impact.

---

### Post by shakin on 2005-12-18
I'm a professional web developer and all I can say is that whoever the developer for the Gap web site is, really needs to get his or her skills up to date. User agent sniffing went out as the favored method for browser-specific coding more than five years ago.

Now, it's best to test for capability. Need the document.all object? Do "if (document.all) {" in your Javascript. Same holds true for anything else.

Truthfully, developing a web site that works with all browsers, including text browsers, is very simple. What's hard is the design because HTML and CSS implementations are so different. There is no reason to prevent someone from accessing your web site just because it won't look right. Simply create a little box at the top of the page informing the visitor that due to their browser choice, the site may look unusual. Creating forms and other elements that absolutely will not work or will not degrade gracefully on all browsers is actually much harder than creating cross-browser code.

Gap should be embarrassed. I'm embarrassed to be in the same profession as these people and half the reason why I posted is to defend the honor of my career. Perhaps they should firmly plant themselves in 1997 and have a "Best viewed in Internet Explorer" icon on their home page.

---

### Post by Casey on 2005-12-18
I sent off the first letter to:
[email]custserv@gap.com[/email]

But got this form letter reply:

> Dear Casey,

Thank you for your e-mail. We apologize for the difficulties you have
experienced on our site. Unfortunately, we have been unable to recreate
the problem you described. It would be helpful if you could provide us
with the information you entered and which page you entered it on, as
well as any error messages you are receiving. Additionally, please
provide the following information:

-which operating system you use:
(for example, Windows 2000, Windows XP, MacOS 9.x, MacOS X, Linux)

-which browser name and version you use:
(for example, Internet Explorer 6.x, Netscape 7.x, AOL 8.)

-connection speed:
(for example, 56K, Cable, T1, DSL)

This information will help us isolate the issue you are experiencing.

Once again, we apologize for any inconvenience we have caused you and
look forward to hearing from you soon.

If we may be of further assistance, please contact us via e-mail at
[email]custserv@gap.com[/email] or by calling 1-800-GAP-STYLE. Our Customer Service
Consultants are available 24 hours a day for your convenience.

Sincerely,

Mindy
Customer Service Consultant

Perhaps we should find a more appropriate email address?  I'll email back the requested details, but we should probably send them somewhere higher up the chain.  Perhaps we can get them to fix this.

---

### Post by jrib on 2005-12-19
Okay they seem to have forwarded my email to their IT department.  They say they are attempting to resolve the issue and give me instructions on spoofing my user agent string.  I guess that's okay, let's see how long it takes them to change a couple of lines of javascript...

Here is their response:
```

Dear Jason,

Thank you for your email.  We apologize for the difficulties you are
experiencing on our site.  Unfortunately, our technical team is aware of
the issue you are experiencing with Linux users being unable to access
our website.  We hope to have this issue resolved soon.

At this time, may we suggest using Mozilla Firefox and updating your
browser configuration as noted below as a workaround to access our site:

1. Open Firefox and enter the url "about:config"
2. Right mouse click in the browser window and select "New->String"
3. Enter "general.useragent.override" (not including quotes) and press
OK.
4. Enter "Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.7.12)
Gecko/20050915 Firefox/1.0.7" (not including quotes) and press OK.

Once again, we apologize for any inconvenience we have caused you.  If
we can be of further assistance, please feel free to contact us again.

Sincerely,

Aaron
gap.com Technical Support

Original Message Follows:
-------------------------

Hello,
When I attempt to access gap.com, I am presented with an error that
states:
>We're sorry, but we do not support the version of the browser you are
using.
>Our site works best with the following browsers:
>
>*PC users*
>Internet Explorer 5.5 and above. Download browser:
http://www.microsoft.com/windows/ie/default.mspx
>Netscape 7 and above. Download browser: http://browser.netscape.com
>Mozilla (including Firefox) 1.0 and above. Download browser:
http://www.mozilla.com/firefox
>
*>Mac users*
>Netscape 7 and above. Download browser: http://browser.netscape.com
>Mozilla (including Firefox) 1.0 and above. Download browser:
http://www.mozilla.com/firefox
However, I am using Firefox version 1.5.  It seems as though the gap
site is
incorrectly blocking me from using the site.  Here is my user agent
string:
"Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8) Gecko/20051111
Firefox/1.5".  When I spoof my user agent string to fool the site into
believeing I am using XP, the site works fine.  I do not understand this
behavior.  Does gap.com not support linux, even though firefox is
equivalent
on both linux and windows XP?
If this is a simple coding error, please forward this to your IT
department
and please let me know if the problem will be resolved before the
christmas
shopping season ends.  If this was intentional, I would appreciate some
sort
of explanation from the representatices of gap.com.
Thank you.
-Jason

```

---

### Post by viscount on 2005-12-28
Ok, eventually I got the same response.

It took them a whlie because I didnt mention anything 
about Linux, just that I was using Firefox and that the webpage wouldnt
load, took them about 5 emails to think to ask what OS I was using.
Then they told me to use the fake hack.

Maybe if enough people keep bugging them they will get it through
their thick skulls.

---

