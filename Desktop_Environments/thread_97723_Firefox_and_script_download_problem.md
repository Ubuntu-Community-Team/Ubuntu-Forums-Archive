---
title: "Firefox and script download problem"
date: 2005-12-01
forum: Desktop Environments
---

### Post by bogoliubov on 2005-12-01
Hello. This has been bugging me for some time; when I use Firefox and want to download some program I simply click the link on the webpage in question. But Firefox shows me the contents of the .run-script instead of downloading it! And it's not always possible to download things by right-clicking...


Does anyone know a solution to this?

---

### Post by bogoliubov on 2005-12-01
I found the nice program "wget", which saved the day. But it's still annoying...

---

### Post by aysiu on 2005-12-01
A good browser always tries to display anything it can--photos, text files, PDFs, etc. If the script is seen as just a text file, it'll be displayed as a text file.

Why doesn't right-clicking always work? I've never had a problem right-clicking and selecting "Save link as..."

---

### Post by bogoliubov on 2005-12-01
[QUOTE=aysiu]
Why doesn't right-clicking always work? I've never had a problem right-clicking and selecting "Save link as..."[/QUOTE]

Sometimes the link is some sort of "download.php" thingy; about which I know absolutely nothing (as my description showed)...

---

### Post by cwaldbieser on 2005-12-01
[QUOTE=bogoliubov]Sometimes the link is some sort of "download.php" thingy; about which I know absolutely nothing (as my description showed)...[/QUOTE]
Those weird extensions (.php, .cgi, .asp, .aspx, .cfm) are all programs that run and generate the HTML content you see when you browse there.  However, if it is a link, you should still be able to right click and do the save as on them.

The real problem is likely that the web server you are connection is not sending the correct content type, so the browser just guesses and displays it as text.

---

