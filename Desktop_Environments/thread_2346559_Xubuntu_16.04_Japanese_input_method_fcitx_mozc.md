---
title: "Xubuntu 16.04 Japanese input method fcitx mozc"
date: 2016-12-16
forum: Desktop Environments
---

### Post by rose.o on 2016-12-16
Because it took me a long time getting the Japanese input method to work under Xubuntu 16.04 I decided to post the steps it took me (I'm new to Xubuntu). Searching online for help never gave me a clear/correct answer. In the end I somewhat used a guide for installing Anthy in Ubuntu to give me an idea of the steps it would take.


If you have Xubuntu 16.04 installed and want to be able to type Japanese, try the following steps:

1. Go to "Settings" and then "Language Support": click the button "install/remove languages" and choose Japanese.

2. Change the "Keyboard input method system" (same menu) to "fcitx". "Close" window.

3. Go to "Keyboard", choose the "Layout" tab, and "Add" Japanese. Make sure "use system default" is untoggled. "Close" window (I'm not sure this step is necessary, but I did it anyway)

4. Go to "Settings" and then "Fcitx Configuration", under the tab "Input method" click "+". Untoggle "only show current language" and choose "Mozc Japanese" from the list. (I had to scroll throught the entire list to find this. It doesn't start with "Keyboard - " like the other options.)

5. Go to the tab "Global config" in the same window and look which keys trigger the Japanese input method. The default on my computer is CTRL+Space. Alternatively, a keyboard icon should be visible in the panel where you can select "Input method" - "Mozc"


I admit to restarting my computer a few times inbetween some of the steps. I'm not sure if it is necessary.
I don't remember ever installing "Mozc" and "Fcitx", I think they came with the system/Japanese language support.

---

