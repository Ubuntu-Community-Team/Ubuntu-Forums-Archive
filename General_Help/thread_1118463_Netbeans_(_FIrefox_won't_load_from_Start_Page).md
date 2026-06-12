---
title: "Netbeans ( FIrefox won't load from Start Page)"
date: 2009-04-07
forum: General Help
---

### Post by sqlpython on 2009-04-07
Although in Both Debian and Kubuntu I have IceWeasel/Firefox set as my default Webbrowser with Kubuntu Firefox will not open without error from a Selection on the Netbeans Welcome Window Pane. A useful Window on the IDE start page as it gives links to "What's New", "MyNetbeans" "Tutorials" and "Flash Tours".

Anyhow it was annoying that with the Debian install IceWeasel opened up fine but with Kubuntu Firefox could not find the url and would produce an error. Yet, with a choice of Konqueror the link would work and open up the Konqueror Browser.

The problem lies with the option switch used to call the URL when starting Firefox 2 or 3. Netbeans 6.5 runs this default string when using a Firefox or Mozilla browser.
firefox -remote "openURL({URL})"
or
mozilla -remote "openURL({URL})"
..
.. This will not work in most cases.
To correct you must change the firefox / Mozilla switch to -new-window "{URL}"
..Do it like so.

Tools > Options > General > See the Web Browser selection
.....Click on [Edit]
With your correct browser selected edit to read
process: /usr/bin/firefox
Arguments: -new-window "{URL}"

Firefox should now pop open to the correct Netbeans page from the Netbeans Startup page.
_________________

---

