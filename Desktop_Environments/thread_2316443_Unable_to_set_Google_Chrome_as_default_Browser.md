---
title: "Unable to set Google Chrome as default Browser"
date: 2016-03-08
forum: Desktop Environments
---

### Post by carelburger on 2016-03-08
After the first installation of Google Chrome it automatically set the default web browser under Settings -> Details -> Default Applications to Google Chrome. I had to change this to Firefox as one of the application did not open links properly in Chrome.

When I tried to set the default browser back to Google Chrome, there was no such option in Settings.

[[img]http://s27.postimg.org/4kdj6751b/Screenshot_from_2016_03_08_10_47_05.jpg[/img]](http://postimg.org/image/4kdj6751b/)

If have tried to rectify the issue with the following commands:

```
sudo update-alternatives --config x-www-browser
```

```
cat ~/.local/share/applications/mimeapps.list

[Default Applications]
text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop
```

```
cat ~/.bashrc

# Default Browser
export BROWSER=/usr/bin/google-chrome
```

Reinstall and purge all Google Chrome settings.

Links still does not open in Google Chrome.

What else can I try?

---

### Post by deadflowr on 2016-03-08
Set it in chrome.
In chrome go to Edit menu, then preferences.
The place to set chrome as the default is at the bottom.

---

### Post by carelburger on 2016-03-08
I have tried this before. It has no effect. Even if I change the default to Firefox it still thinks it is the default browser.

> **deadflowr said:**
> Set it in chrome.
In chrome go to Edit menu, then preferences.
The place to set chrome as the default is at the bottom.

---

### Post by carelburger on 2016-03-11
I was able to fix the issue.

```

gedit ~/.config/mimeapps.list

```

Change all **firefox.desktop** to **google-chrome.desktop**.

---

