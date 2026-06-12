---
title: "ubuntu 14.04 keyboard shortcuts to change input layout"
date: 2014-06-29
forum: Desktop Environments
---

### Post by nick_m2 on 2014-06-29
Hi all,

In Ubuntu 14.04, if  I want to create a custom shortcut in the “Keyboard” settings to switch  the current keyboard layout to a specific keyboard layout (such as  Arabic, Greek, or Persian), what command should I type in the “Command: ”  field of the “Custom Shortcut” menu? Or is there a better way?

I believe this was possible previously, but I  can’t find the appropriate settings now. I don't know whether this is important, but I’ve  set the keyboard input method system to ibus through the “Language  Support” menu. I’ve also set the “show current input source in the menu  bar” through the “Text Entry Settings” menu. 

I’d like to set up shortcuts similar to the following. These are the shortcuts I used on my previous system:

left alt+shift+1: English (US)
left alt+shift+2: Pinyin (Chinese simplified)
left alt+shift+3: Hangul (Korean)
left alt+shift+4: Anthy (Japanese)
left alt+shift+5: Arabic

left ctrl+shift+1: English (International AltGr dead keys)
left ctrl+shift+2: Chewing (Chinese traditional)
left ctrl+shift+3: Russian (phonetic)
left ctrl+shift+4: Greek
left ctrl+shift+5: Persian

I  tried assigning custom shortcuts through the “Keyboard” settings, but I  couldn’t get it to work properly. For example, I created a custom  shortcut, typed “Greek” in the “Name” field, and typed the following in  the “Command” field:

ibus engine xkb:gr::gr

I  then assigned the shortcut left ctrl+shift+4. After opening a word  processing application and typing the shortcut, I was then able to type  in Greek, but the input source in the menu bar still said “English” even  though I was typing in Greek. Moreover, I couldn’t get the shortcuts to  work with Russian. I think it might be because I chose the  wrong commands (I found them by reading the info pages for ibus and  ibus-daemon in the terminal).

Thanks for your help!

---

