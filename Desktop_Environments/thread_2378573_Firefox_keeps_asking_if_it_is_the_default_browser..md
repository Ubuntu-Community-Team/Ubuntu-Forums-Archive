---
title: "Firefox keeps asking if it is the default browser."
date: 2017-11-24
forum: Desktop Environments
---

### Post by peter235 on 2017-11-24
I have a problem with the way Firefox thinks it is default browser. I typically initiate Firefox in one of two ways:

(1) via a menu item to which is attached a firefox.desktop file
(2) by clicking on a link in an email in Thunderbird which is configured to load the firefox application directly, not via the .desktop file.

Every time I switch between these two methods, Firefox asks me whether to confirm Firefox is the default browser. If I stick to just one of the two invocation methods, it does not repeat the request for confirmation. Presumably it is storing the information it uses to know it is the default browser differently depending on how firefox is invoked, but I have failed to figure out where these settings are stored. Some help with this would be most appreciated.

Versions are:

Ubuntu 16.04
Firefox 56
Thunderbird 52.4.0

---

### Post by #&amp;thj^% on 2017-11-24
How is set under "about:config" in your URL Bar
Look for "browser.shell"
And make sure it is set to your desired preference.

---

### Post by walts48 on 2017-11-25
Did you set Firefox as your default browser in Preferences > General > Startup?

---

### Post by peter235 on 2017-11-25
**1fallen**: not clear how this answers my query. Where does Firefox record that it is the default browser? Are the about:config setting you refer to the answer? If so how do they work? In particular, which specific entry means "Firefox knows it is the default browser"? And why would this setting change when I switch invocation method?

**walts48**: I am a bit confused about your question and would be grateful if you would clarify further. In Preferences > General > Startup you have the following settable options:

1. Always check if Firefox is your default browser?
2. When Firefox starts - select from "show your home page", " show a blank page" and "show your windows and tabs from last time"
3. Home page: enter a url or click one of the button "Use current pages", "Use bookmark" or "Restore to Default"

None of these specifically allows you to specify that Firefox is your default browser. The first question simply instructs Firefox to check this when it starts. I do have this option selected and I presume this leads to the scenario outlined above in which Firefox asks me whether it should be set as the default browser, when it starts. My question is however, having confirmed this once, why would it re-ask this question when I switch invocation method?

---

### Post by #&amp;thj^% on 2017-11-25
The method I showed you "should" stop it from re-asking this question when you switch invocation methods. (If not, there is something amuck)
There is also a way in your Desktop System Settings>>>Preferred Applications..for setting it as default also. (But it sounded to me that you already had tried that)

---

### Post by mc4man on 2017-11-25
Set ff as default in firefox
Open up ~/.config/mimeapps.list in text editor, leave open
Do your different things, see if any of the defaults for browser change, if so, to what & which changes.
(- thunderbird generally  only uses x-scheme-handler/http= & x-scheme-handler/https=

(- all of the browser related mimetypes should =firefox.desktop

---

### Post by walts48 on 2017-11-26
@peter235

Type about:profiles in the address bar and press Enter.
Do you see a "Set as default profile" button under the profile in use? If you do click the button.

---

