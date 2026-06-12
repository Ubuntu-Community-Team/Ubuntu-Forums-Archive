---
title: "Parameters on Default Web Browser"
date: 2013-12-08
forum: Desktop Environments
---

### Post by raptir on 2013-12-08
I'm using Xubuntu and want to make Chrome by default browser. However, I run chrome with the --disk-cache-dir=/tmp/chrome in order to move the cache into a ramdisk. I've modified the .desktop file for chrome to run with the parameter and it works fine. However, when I set my default browser to be "/usr/bin/google-chrome-beta --disk-cache-dir=/tmp/chrome" the Web Browser shortcuts still opens Chrome with the cache in the default location. From a little Googling, it seems as though exo-open ignores any parameters on the default application. Is there any way around this?

---

### Post by Toz on 2013-12-08
Have you tried bypassing the exo-open set of commands by creating your own entry in Preferred Applications as documented at [http://docs.xfce.org/xfce/exo/preferred-applications]("http://docs.xfce.org/xfce/exo/preferred-applications")?

---

### Post by raptir on 2013-12-09
Yes, unfortunately what you linked to does not bypass exo-open. When you click a link or run the Web Browser application Xfce calls "exo-open --launch WebBrowser" which takes the browser command entered in the preferred applications window and strips off any parameters.

*The special marker %s in the command will be substituted with the URL when you click on a hyperlink. **When running just the preferred Web Browser without any URL, i.e. using exo-open --launch WebBrowser, only the binary of the specified command will be used and the parameters will be stripped off.** In the example above, with mywebbrowser &#8221;%s&#8221; as custom Web Browser, the command mywebbrowser will be used to open the Web Browser without an URL.*

It does not specify it in the page you linked, but I've found that exo-open also fails to parse parameters when clicking a URL. It passes the URL but still drops the remaining parameters.

---

### Post by The_ERROR on 2013-12-19
I have exactly same problem.... so far no luck...

---

