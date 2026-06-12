---
title: "Identifying as Microsoft Internet Explorer under Ubuntu"
date: 2006-02-25
forum: Desktop Environments
---

### Post by sas13 on 2006-02-25
My bank won't let me into their website with any browser other than IE, which poses obvious problems.....

I've tried using wine, but haven't had very much success - IE keeps crashing, and besides I'm fairly sure I'll need flash to view the website, and I don't think IE under wine  could handle that.

I've also partialy tried using a couple of browsers that have an "identify as" option - konqueror using KNOPPIX (I use gnome and didn't want to install all the extra stuff you need for konq). Anyway that didn't fool anyone (neither the bank website nor [www.danasoft.com/sig)](www.danasoft.com/sig)). I also wanted to try Opera but was not succesful in installing it.

is there any way to get the website to let me in?

it's too much trouble to reboot twice just to access one website, plus I don't want to put up with this discrimination!

---

### Post by cotcot on 2006-02-25
I have installed opera successfully according to the ubuntu wiki howto ( [https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser) ). 
In opera you have the option "identify as". You can see/change it by pressing F12 (or >tools>quick preferences : bottom of the window).
It works by me.

---

### Post by Madpilot on 2006-02-25
Opera's "Identify As IE" feature doesn't seem as sucessful at spoofing websites under Linux as it was under Windows for me.

I suspect this is because Opera's UA still mentions Linux, but I haven't bothered investigating further...

sas13, I'd recommend changing banks. Mine has always worked with non-IE browsers in both Windows and Linux, and when it stopped working I wrote them a fairly blunt email and it was fixed inside a week...

---

### Post by heimo on 2006-02-25
[quote=sas13]is there any way to get the website to let me in?[/quote]
Installing this plugin...
[https://addons.mozilla.org/extensions/moreinfo.php?id=59](https://addons.mozilla.org/extensions/moreinfo.php?id=59)
... gives you a new submenu under Tools -> User Agent Switcher. It's possible that also the incredibly useful webdeveloper plugin (available from Ubuntu repositories: firefox-webdeveloper) can do this.


[quote=sas13]it's too much trouble to reboot twice just to access one website, plus I don't want to put up with this discrimination![/quote]

Personally, I would move to another bank which doesn't have such narrow view on computer technology and standards and complain to my ex-bank. (It won't change much, but they need to know they're losing customers.) I would probably also write an email to my local EFF organisation. But that's me.

---

### Post by SamH on 2006-02-25
I'm not saying they will roll over.....but....

Contact your bank and COMPLAIN!!!

They probably contract out to a webservice provider that is too lazy to code for true internet compatibility.  They're probably using MS FrontPage.

The bank has no clue unless people start telling them, "You're about to lose my business because........"

Talk to your businesses.  Tell them about open standards.  Other wise most won't know any better than to use MS.

---

### Post by sas13 on 2006-02-25
Thanks cotcot,

That link sorted out my opera problems!

But I'm not sure if it solved the real problem-

Using opera posing as IE6 I didn't get the "please use MS IE" page, but went straight to the login screen. (this didn't work with konqueror!)

unfortunately that's as far as I got :(

to be honest though I might not be using the correct password :???:

I guess I'll go boot into windows and see if that's all it is...

BRB

---

### Post by Trab on 2006-02-25
try the firefox plugin user agent switcher... has yet to fail for me!

yeah, check in windows, if it works there, make sure u know ur UN and PW...
then try the user-agent-switcher in Firefox...

---

### Post by aysiu on 2006-02-25
Firefox is *the* up and coming browser in the world (supposedly at 10% of the "market" share for web browsers). Any bank that requires Internet Explorer isn't worth banking with.

I know it sounds extreme (changing info, waiting for new checks to arrive, etc.), but it's worth switching banks for this, and it'll send your bank the message that it can't continue to force its customers to use Internet Explorer.

My wife and I use major banks (not weird obscure ones), and they both work fine in Firefox (no need to "identify as" anything).

---

### Post by sas13 on 2006-02-25
wwwhhhhooooaaa!!!!

booted into windows, logged on to website, booted back -  SIX replies waiting!!

I guess a lot of people know what I mean about the discrimination thing...

anyway, 

1 - turns out I had the right password.

2 - opera did the same thing under windows as it did under linux; no "please use MSIE" page but also no luck signing in.

I'll check out the firefox plugin now (searched for something like that but couldn't find it before)

as far as complaining to the bank,
of course you guys are all right, and I was thinking I'd do that. 

The only thing is that the bank is in Israel and I'm living in the US  now, so it'll be quite a hassle to switch banks, and also I think it might be harder to get anyone care over there.... oh well.

---

### Post by aysiu on 2006-02-25
[QUOTE=sas13]
I'll check out the firefox plugin now (searched for something like that but couldn't find it before)[/QUOTE] I'll vouch for the User Agent Switcher extension--it's never failed me before.

That said, how did you install IE using Wine? I've found [IEs4Linux](http://www.tatanka.com.br/ies4linux/en/instructions/) is pretty easy to use. I'm trying to remember whether it does Flash...

**Edit**: Yes, it does! > The magic of IEs4Linux is to use full browsers downloads instead of using that boring install process. The script automatically downloads full versions of IE from the Evolt Browser Archive. Then installation is done completely behind the scenes! You don&#8217;t need to click on anything to install IE6, IE5.5 and IE5 - with FlashPlayer 8!

---

### Post by sas13 on 2006-02-25
ok, no luck.

that firefox plugin seems to work extremely well - it even fooled microsoft. I have a hotmail account subscribed to their beta "windows live mail" to check that out. of course no surprises, using anything but MSIE there you get a "please use IE to enjoy the full functionality blah blah blah..." message - well the plugin had them thinking I was using IE.

BUT...

both the windows live page and the bank webpage didn't actually work properly - buttons are displayed on screen but it is impossible to actually push them and things like that.

so I could again get to the login screen at the bank, fill in my username and password, but was then unable to press the  submit button...

I guess that doesn't leave many options other than complaining to the bank.

---

### Post by sas13 on 2006-02-25
aysiu,

thanks for the tip about IEs4Linux,
I just installed wine today, and made a bit of a mess of it, but I'll go back and clean up and see if IEs4Linux does the trick.

it looks like ultimately I can fool the website into thinking I'm using IE but there is something in their coding that only IE actually understands. So maybe wine is the solution after all

---

### Post by Trab on 2006-02-25
it might be your banks site...
i would ask you to post it, but that might be a security risk...
or something...
sorry mate
ask your bank why there site sucks?
did it work while u were in windows?
latz
-Trab

---

### Post by aysiu on 2006-02-25
[QUOTE=sas13]
it looks like ultimately I can fool the website into thinking I'm using IE but there is something in their coding that only IE actually understands.[/QUOTE] If that "something" is ActiveX then even IE in Wine isn't going to help you.

---

### Post by ardchoille on 2006-02-25
Complain to your bank. If they see that they are losing customers, they might just see it as a way to expand their services. It can't hurt :)

---

### Post by sas13 on 2006-02-25
ok, I installed MSIE using IE24Linux,
it'll let me surf to some basic sites, but a lot of fancier websites just cause it to crash - unfortunately this includes my bank's website.

So I will be complaining to my bank, but it looks like until they change something on their end I'm stuck.

too bad, because I'm finally at the stage where the only reason I ever use windows any more is for exactly two websites - my bank, and another related to my girlfriend's work.

I know there are other websites that work only with IE, but I'm perfectly happy to do without them. But these two I've got no choice about.

so I guess unless anyone has a suggestion I haven't tried the only thing left is to wait for (and push for) these guys and others to evolve and realize there's a lot of other stuff out there aside from MS.

anyway, thanks a lot for everyone's help!

---

### Post by Scunizi on 2006-03-03
I tried the user agent switcher for a site I have to use for work.  Although I was able to log in and the site looked great, the functionality was totally broken and unusable.  There are thousands of people using this site with lots of complaints about being stuck with IE but they have resisted making any changes.  :evil:

---

