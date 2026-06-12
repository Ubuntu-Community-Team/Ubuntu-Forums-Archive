---
title: "How to set default web browser?"
date: 2018-10-27
forum: Desktop Environments
---

### Post by pudens on 2018-10-27
Hi!

I'm totally new to Lubuntu and LXQt, and I have one question. Lubuntu comes with Firefox. I've installed Chromium, goes to LXQt session settings, set Chromium as default web browser and... Nothing. Firefox always stays as default. Please help. :)

---

### Post by ajgreeny on 2018-10-27
Firefox stays default in what way; how have you deduced that fact?
Perhaps you need to change the default application to open .html files by right clicking on any html file in pcmanfm ->Properties then make a change in the Open with part.

If it's links in emails that still take you to firefox you will need to make changes in the email app configuration.

---

### Post by Dennis N on 2018-10-27
Tip for LXQt:

You can check default applications for mime types (content type)  from **Preferences > LXQt Settings > File Associations**. You get an nice GUI that allows you to easily change the application for a mime type (see attached screenshot for an example). Mime type for web pages is text-html; here it's set to Firefox.

---

### Post by pudens on 2018-10-27
In LXQt session settings always Firefox stays as default web browser. When I start Chromium, always appears info "Set chromium as default browser?". So I suppose, that Firefox stays as default web browser.

---

### Post by pudens on 2018-10-28
> **ajgreeny said:**
> Firefox stays default in what way; how have you deduced that fact?

So, nothing changed. Of course, i set default app for opening HTML. But Chromium always pops up on start with info, that "Chromium is not default browser" and asks for setting it default. Changing in LXQt session settings nothing changes. I mean this window (screen is from internet, I'm now in work, so I have no access to my computer to make own) - see attachment. I change Firefox in "web browser" to Chromium, but when I call that setting again, Firefox remain as concrete... :)))

---

### Post by Dennis N on 2018-10-28
You might use this command and see what it gives you. It will tell you what's the system default browser, which may be the one used when links are opened from within other applications (maybe a link in LibreOffice, for example).

```
update-alternatives --get-selections | grep x-www-browser
```

Here is mine, showing firefox:
```
dmn@Sydney:~$ update-alternatives --get-selections | grep x-www-browser
x-www-browser                  auto     /usr/bin/firefox

```

Please post your result. If it's not showing what you want, it can be changed from terminal.

---

### Post by pudens on 2018-10-29
> **Dennis N said:**
> Please post your result. If it's not showing what you want, it can be changed from terminal.

Thanks, Dennis. The result was firefox, and I found this:

```
[COLOR=#242729][FONT=Consolas]sudo update-alternatives --config x-www-browser[/FONT][/COLOR]
```

And I set Chromium as default. But I still don't know, why I can't do it from GUI... :)

---

