---
title: "Epiphany and tabs"
date: 2005-10-02
forum: Desktop Environments
---

### Post by Confuse on 2005-10-02
Is there a way to get epiphany to open by default in a new tab instead of using a new window? And I don't mean middle clicking to get a new tab. Any help is appreciated. Thanks!

---

### Post by zAo on 2005-10-03
[QUOTE=Confuse]Is there a way to get epiphany to open by default in a new tab instead of using a new window? And I don't mean middle clicking to get a new tab. Any help is appreciated. Thanks![/QUOTE]
Browse to about:config an filter on "tab", change the setting you like and 'voila'!

---

### Post by Confuse on 2005-10-03
[QUOTE=zAo]Browse to about:config an filter on "tab", change the setting you like and 'voila'![/QUOTE]

I tried this. All the settings I could, still no go. ;[

---

### Post by jslmg on 2008-01-07
I do hope that Epiphany's developers read these forums, cuz this is the most requested feature. Truth is, it is not implemented "yet" in Epiphany.

---

### Post by schmolch on 2008-01-07
It's requested on their mailinglist since a long time.

---

### Post by jslmg on 2008-01-07
Stop the presses!

Suddenly, new links are opening in tabs! I must have found the right settings, quite accidentally, and I'm not changing anything again, ever!

I'm not sure I can replicate what I did though.

I think the problem here is that the "open links in tab" feature technically is implemented, but it is buggy and prone to conflicts. 

I'll review all the settings I have in gconf and/or Preferences/Preferred Applications, and report them here soon...

---

### Post by jslmg on 2008-01-07
The settings I have are nothing different from what's been reported on various threads. But here's a summation, all in one place:

(1) First, close all Epiphany windows, and make sure there are no Epiphany processes running. 

Open Applications-->System Tools-->Configuration Editor, then:

(2) Go to /apps/epiphany/general.

(3) Check "always_show_tabs_bar"

(4) Go to /desktop/gnome/applications/browser.

(5) Make sure the value of "exec" is "epiphany" (no other commands after it in this field)

(6) Make sure "nremote" is checked. (don't know if this is relevant, but it is checked in my case)

(7) Go to /desktop/gnome/url-handlers/about. The next three steps will ensure that Epiphany is the default browser--apparently necessary for links to open in tabs:

(8 ) Make sure the value of "exec" is ```
epiphany --new-tab %s
```.

(9) Go to /desktop/gnome/url-handlers/http.

(10) Make sure the value of "exec" is ```
epiphany --new-tab %s
```.

(11) Make sure "enabled" is checked.

(12) Go to /desktop/gnome/url-handlers/https.

(13) Make sure the value of "exec" is ```
epiphany --new-tab %s
```..

(14) Make sure "enabled" is checked.

(15) Close configuration editor, and go to  Settings-->System-->Preferences-->Preferred Applications.

(16) Confirm that "Web Browser" is "Epiphany Web Browser," that "Open Link in New Tab" is marked, and that the command field says: ```
epiphany --new-tab %s
```

(17) Close Preferred Applications, and launch Epiphany.

(18 ) Open your email client and find a message you trust that has an http:// link. Click, and see if it opens a new tab in Epiphany. In my case, Epiphany does not come to the front, so you may have to bring it to the front in your dock or panel.

(19) If the link did not open in a new tab, try restarting the computer.

Optionally, you may want to try opening a terminal, then launching sudo gconf-editor, then repeating all the steps above in root. 

Hope it works!

---

