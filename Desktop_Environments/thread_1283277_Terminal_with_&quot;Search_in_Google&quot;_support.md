---
title: "Terminal with &quot;Search in Google&quot; support"
date: 2009-10-05
forum: Desktop Environments
---

### Post by msaitozen on 2009-10-05
Hi,

I have a question about terminal. I can search any selected thing at terminal in Google while using MacOSx terminal. Is there any support like this while using Ubuntu? If not, any plan to add this support to ubuntu ? :confused:

---

### Post by kanikilu on 2009-10-05
I don't know of any built-in way to do this. It can be done with a pretty simple shell-script, though:

```
#!/bin/bash
baseurl="http://www.google.com/search?q="
query="$@"
url=$baseurl$query
/usr/bin/firefox $url &
```

Just save this file as "google" (no extension), somewhere in your PATH and make it executable (chmod +x google). Now you can open a terminal and type:
```
google search+terms
``` Note: Use a plus (+) sign between search terms instead of a space. I'm sure someone who knows bash scripting above my novice level could automatically convert spaces to a plus sign.

This might be more effort than you're willing to put into getting search functionality in the terminal, but figured I'd at least throw that out there...

---

### Post by c0mput3r_n3rD on 2009-10-05
uuse lynx web browser.  just type lynx in terminal, after you "sudo apt-get install lynx"

---

### Post by luigi_mb on 2009-10-05
> **msaitozen said:**
> Hi,

I have a question about terminal. I can search any selected thing at terminal in Google while using MacOSx terminal. Is there any support like this while using Ubuntu? If not, any plan to add this support to ubuntu ? :confused:

Try "googlizer". It's in the repos. Once installed, you can create a custom launcher on one of the desktop panels. Select any word or sentence in any application, click on the Gogoglizer icon, and your Google search hits will be displayed in your default browser.

---

### Post by umpirsky on 2012-09-05
[http://blog.ubuntu-tweak.com/2010/11/16/gnome-terminal-with-google-search-support.html](http://blog.ubuntu-tweak.com/2010/11/16/gnome-terminal-with-google-search-support.html)

---

### Post by nothingspecial on 2012-09-05
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

