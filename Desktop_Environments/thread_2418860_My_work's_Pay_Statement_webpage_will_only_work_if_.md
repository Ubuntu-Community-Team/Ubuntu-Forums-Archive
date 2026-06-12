---
title: "My work's Pay Statement webpage will only work if I use Windows/Mac. Why?"
date: 2019-05-12
forum: Desktop Environments
---

### Post by greg2lapa on 2019-05-12
I started working at a retail store. To view my pay statements from home, I can go to the retail store's www address on the web and type my login info. I get a "Microsoft sign-in" 2nd factor phone-call/text and once I respond to that then I am logged in.

When I login from Debian or Ubuntu (using either Chrome, Chromium, or Firefox), I am taken to a blank page that says Oracle at the top and has a click through menu but none of the menu destinations work. They always lead to "This site can&#8217;t be reached" or refused to connect messages.

If I try logging in using the exact same process with Windows or iOS or Mac, using Chrome, Firefox, and/or Safari, I am taken to a nicely designed webpage with "tiles" to click on, which allows me to view my pay statements. 

So it's not the web browser. The site will only work with Windows or iOS or Mac. Why?

I want to call up HR of the company and complain but I would like to be able to state why it's not working with Linux. What exactly is the company doing that is preventing this website from working and is it fair that the company's site is behaving this way? I assume they could support Linux if they wanted or is it more complicated that that? (I don't know if it will work with Android but I assume it will).

---

### Post by yetimon_64 on 2019-05-13
> **greg2lapa said:**
> ...So it's not the web browser. The site will only work with Windows or iOS or Mac. Why?...

Actually it most likely is the web browser's "user agent string" which is identifying the OS as well as the browser in use by yourself to the site you are connecting to.

It appears you will need to use the extension "user agent switcher" in Firefox when trying to access the site from a linux box.

To give you an idea how it works I have attached four screenshots. The browser in use is firefox on ubuntu mate 18.04 with the user agent switcher extension installed. The first screenshot shows the switcher and the choices available...
 [ATTACH=CONFIG]283247[/ATTACH]
The next 3 screenshots show me on [COLOR=#0000ff][noparse]https://www.whoishostingthis.com/tools/user-agent/[/noparse][/COLOR] (note the url is disabled in this post, you will need to copy/paste it from here to your browser address bar if you wish to test the user agent switcher extension with it).

The first shows me as coming from chrome on linux, the second from chrome on windows, the third from firefox on windows...
[ATTACH=CONFIG]283248[/ATTACH]  [ATTACH=CONFIG]283249[/ATTACH]  [ATTACH=CONFIG]283250[/ATTACH]

Rather amazingly if I try to be honest and set firefox on linux (which is actually what I'm using) the re-captcha challenge tells me to use a supported browser but works if I tell them I'm on firefox in windows ;-).
> What exactly is the company doing that is preventing this website from  working and is it fair that the company's site is behaving this way? As for "fair", it is a relatively common practice Linux users are well used to dodging. 
When you connect to their server they not only know what browser you use but also which OS you are using it on from the user agent string. They can be very easily fooled into thinking you are on Windows or Mac with a user agent switcher extension though.

I can't guarantee all sites will work fully with user agent switcher, but if this is because of some site admins arbitrary decision to NOT support Linux OSes then user agent switcher may be of use to you, good luck. 
[B]
Edit:[/B] if you use the user agent switcher while logged in here you will need to re-login after any changes. I've been dropped out of this forum about 4 times while composing this post and testing user agent switcher settings. Be aware of this if you use the extension.

Regards, yeti.

---

### Post by &amp;KyT$0P# on 2019-05-13
Did you try overriding your user-agent string on the Linux browsers?

In Firefox:

1) go to about:config

2) right-click > New > String
name: [FONT=Courier New]general.useragent.override[/FONT]
value (assuming you're using Firefox 66.x on Linux):
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:66.0) Gecko/20100101 Firefox/66.0
```

This will make Firefox identify as Firefox 66.0 64-bit on Windows 10 64-bit.

It will apply right away, but changing user-agent string in the middle of a browser session might log you out of websites.  You might consider clearing cookies and restarting the browser after making this change.

(If this doesn't help, go back to about:config > right-click the [FONT=Courier New]general.useragent.override[/FONT] entry > Reset, to get back the default user-agent string.)


* oops, yetimon_64 beat me to it :)

[s]Last I checked, WebExtensions for switching user-agent could not be fully reliable in Firefox.  This was due to limitations of Firefox's WebExtensions system - it's not the extensions' fault.  It may have been fixed since I last checked?[/s]
**Edit: Quick check in Firefox 66.0.5 looks like yes, this was fixed.**

yetimon_64, could you please link the specific extension you have in mind, so that I can test it on current Firefox?

Anyway, you can definitely use the [FONT=Courier New]general.useragent.override[/FONT] method for reliable diagnostics, and if it works, then decide if you want to try an extension.

---

### Post by yetimon_64 on 2019-05-13
> **halogen2 said:**
> ...
yetimon_64, could you please link the specific extension you have in mind, so that I can test it on current Firefox?...

[[COLOR=#0000ff]--This one--[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher-revived/?src=search") was the first one returned when I searched extensions from the "Tools>Add ons" menu in firefox. Named "User-agent switcher" by "Linder". This is being used here on "Firefox Quantum 66.0.4" on Ubuntu Mate 18.04 (64 bit).

**Edit**: I just updated my system and Firefox Quantum is now at version 66.0.5 and the user-agent switcher extension still works fine after further testing on the test site url in post #2.
**Edit 2:** [s]After you finish using the extension to access a site as another OS or browser it pays to disable the user-agent switcher rather than setting it back to linux and firefox. I just had a site (github) tell me I am using an unsupported browser.[/s]**(see post 6, user-agent string can be edited)** It appears the firefox/linux setting in the extension may be using an older user agent string than is current for firefox. [s]After disabling the extension the github site stopped complaining about my browser being out of date. It may pay to use halogen2's method after seeing this effect OP.[/s]

---

### Post by greg2lapa on 2019-05-13
> **yetimon_64 said:**
> Actually it most likely is the web browser's "user agent string" which is identifying the OS as well as the browser in use by yourself to the site you are connecting to.

It appears you will need to use the extension "user agent switcher" in Firefox when trying to access the site from a linux box. . . .

Regards, yeti.

Yeti, I installed the User-Agent Switcher by Linder and selected Firefox on Windows and it worked!

Thank you so much for your direction and help. I can't thank you enough. It was very kind of you to respond and your help solved my issue. 

To make sure I understand correctly, the reason Linux won't work is because someone on the server end made a "conscious" decision to set a specific user-agent requirement that disallowed Linux? Or is it possible it was just lack of attention to detail and it was a default setting or something that somebody didn't bother changing? I have no experience with configuring this kind of server setting. I'm wondering if I can know if it was an intentional exclusion of linux or just someone too lazy to look over settings or something.

---

### Post by &amp;KyT$0P# on 2019-05-13
> **yetimon_64 said:**
> [[COLOR=#0000ff]--This one--[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher-revived/?src=search") was the first one returned when I searched extensions from the "Tools>Add ons" menu in firefox. Named "User-agent switcher" by "Linder".

Thanks for the link.  Looks like a good recommendation for this case.  It seems reliable in Firefox 66.0.5.

> After you finish using the extension to access a site as another OS or browser it pays to disable the user-agent switcher rather than setting it back to linux and firefox. I just had a site (github) tell me I am using an unsupported browser. It appears the firefox/linux setting in the extension may be using an older user agent string than is current for firefox. 
Yes, it's spoofing very old Firefox version by default -
```
  "firefox": {
    "windowsd": "Mozilla/5.0 (Windows NT 10.0; WOW64; rv:56.0) Gecko/20100101 Firefox/56.0",
    "mac": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.12; rv:56.0) Gecko/20100101 Firefox/56.0",
    "linux": "Mozilla/5.0 (X11; Linux i586; rv:31.0) Gecko/20100101 Firefox/31.0",
    "chromeOS": "Mozilla/5.0 (X11; U; CrOS i686 9.10.0; en-US) AppleWebKit/532.5 (KHTML, like Gecko) Gecko/20100101 Firefox/29.0",
    "ibm": "Mozilla/5.0 (OS/2; U; Warp 4.5; en-US; rv:1.7.12) Gecko/20050922 Firefox/1.0.7",
    "freebsd": "Mozilla/5.0 (X11; FreeBSD amd64; rv:40.0) Gecko/20100101 Firefox/40.0"
  },
```

But at the bottom of the popup is a pencil icon, click that and you can manually edit the user-agent it's spoofing.

It also has the option to limit user-agent switching to specific domains or URL prefixes.  This might be more convenient for the OP than enabling/disabling the addon.

> **greg2lapa said:**
> I'm wondering if I can know if it was an intentional exclusion of linux or just someone too lazy to look over settings or something.

I think the only way to be sure whether this is intentional or not is to ask the server administrators.

---

### Post by yetimon_64 on 2019-05-13
> **halogen2 said:**
> ...
But at the bottom of the popup is a pencil icon, click that and you can manually edit the user-agent it's spoofing.

It also has the option to limit user-agent switching to specific domains or URL prefixes.  This might be more convenient for the OP than enabling/disabling the addon.
Good to know that, thanks halogen2. Agreed, that would be a better idea for the OP. I'll look into manually editing that here myself next time I need to use it. **Edit:** the user agent string here is now edited to the current browser value and the re-captcha on the test site works with linux/firefox.

> **halogen2 said:**
> I think the only way to be sure whether this is intentional or not is to ask the server administrators.+1.

---

