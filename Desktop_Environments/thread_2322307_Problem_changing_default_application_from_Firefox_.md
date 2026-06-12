---
title: "Problem changing default application from Firefox to Chromium (v. 16.04)"
date: 2016-04-27
forum: Desktop Environments
---

### Post by tony119 on 2016-04-27
I have a new install of Lubuntu 16.04.  I have attempted to change the default web application for LXSession > Launching applications > webbrowser from Firefox to Chromium (preferable: "chromium-browswer --incognito") but the default override still opens Firefox.  I also use text applications like surfraw, but when I configure it to open links in Chromium it still overrides my preference and opens Firefox.  Is there another configuration setting I can change to stop Firefox from being the default web application and instead use Chromium?

---

### Post by vasa1 on 2016-04-27
What do you see with *update-alternatives --get-selections | grep -i browser*?

```
08:04 PM ~ $ update-alternatives --get-selections | grep -i browser
gnome-www-browser              auto     /usr/bin/google-chrome-stable
infobrowser                    auto     /usr/bin/info
www-browser                    auto     /usr/bin/w3m
x-www-browser                  auto     /usr/bin/google-chrome-stable
08:04 PM ~ $ 
```

And did you take a look at *man surfraw*? It has this:```
       -browser=EXECUTABLE
              Set browser (default: sensible-browser).
```and this:```
       SURFRAW_graphical_browser
              Name/path  of  graphical  browser  executable.    e.g   mozilla,
              netscape etc.

              Default:

               def SURFRAW_graphical_browser sensible-browser

```

---

### Post by tony119 on 2016-04-27
@vasa1

checking update-alternatives the gnome-www-browser and x-www-browser were pointed to firefox.  I've modified it now so the output is:

```

~$ update-alternatives --get-selections | grep -i browser
gnome-www-browser             manual   /usr/bin/chromium-browser
infobrowser                    auto     /usr/bin/info
www-browser                    auto     /usr/bin/links
x-www-browser                  manual   /usr/bin/chromium-browser

```

Using my surfraw config file from my previous Lubuntu OS

.config/surfraw/conf 

```

BROWSER="chromium-browser --incognito"

```

It will now open up using chromium browser, but it still prevents me from using the "--incognito" option that I had been using previously in the conf file.

I've noticed that I can even issue the command

```

$ x-www-browser --incognito

```

And it will open up "--incognito" as desired.  But if I try to define it in the surfraw config file, it is still overrides without the "--incognito" option.

---

