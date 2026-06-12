---
title: "Typing Korean (Hangul)"
date: 2009-01-07
forum: General Help
---

### Post by mssever on 2009-01-07
I'm going to be moving to Korea, so naturally I'll need to learn Korean and have the ability to type Korean. However, I've been unable to figure out how to type in Korean. I've tried installing all the Korean language-support packages, and I've added the Korean 104-key compatible keyboard layout, but when I try to type, I get Roman characters. I booted up the Ubuntu live CD in a VM and selected Korean at the boot menu. In such an environment, I expected everything to be configured correctly out of the box. But I still got Roman characters in the live CD environment. Why is this so hard? What am I doing wrong?

---

### Post by mssever on 2009-01-08
I've made some progress. In Gnome apps, I can right click on a text entry and find an input methods submenu. By choosing "SCIM Input Method" from the options listed, I can type Korean--regardless of my selected keyboard layout. However, that menu entry isn't available in non-Gnome apps such as Firefox and OpenOffice--which are the most important apps that I use for these purposes. So there must be a better way.

Surely there's a system-wide way to do this that works in every program! What is it?

---

### Post by mssever on 2009-01-08
I've made some progress. In Gnome apps, I can right click on a text entry and find an input methods submenu. By choosing "SCIM Input Method" from the options listed, I can type Korean--regardless of my selected keyboard layout. However, that menu entry isn't available in non-Gnome apps such as Firefox and OpenOffice--which are the most important apps that I use for these purposes. So there must be a better way.

Surely there's a system-wide way to do this that works in every program! What is it?

---

### Post by moon2js on 2009-01-11
I type in Firefox all the time in Korean. I don't think I did anything special to type Korean. Make you sure you enable it in Language Support and check the complex characters box (which I think is just SCIM, which you apparently already installed).

There should be a keyboard icon in your tray, and you can click that to manually switch input methods. Configuring SCIM is really confusing, but you can also change the shortcuts.

What'd I'd like to know is the best way to remap my keyboard. I have a U.S. keyboard, but I'd like to make it act more like a Korean keyboard; I'd like remap the right Alt key to &#54620;&#50689; (a Korean-English one-button input method switch) and remap the Alt to the right Windows meta key.

I'm trying to think if that interferes with anything (I never use the Windows meta keys, or maybe I don't know what they're for, and I don't think I use the right Alt key) and figure out how to remap keys like that at the moment.

---

### Post by mssever on 2009-01-14
> **moon2js said:**
> I type in Firefox all the time in Korean. I don't think I did anything special to type Korean. Make you sure you enable it in Language Support and check the complex characters box (which I think is just SCIM, which you apparently already installed).

There should be a keyboard icon in your tray, and you can click that to manually switch input methods. Configuring SCIM is really confusing, but you can also change the shortcuts.

What'd I'd like to know is the best way to remap my keyboard. I have a U.S. keyboard, but I'd like to make it act more like a Korean keyboard; I'd like remap the right Alt key to &#54620;&#50689; (a Korean-English one-button input method switch) and remap the Alt to the right Windows meta key.

I'm trying to think if that interferes with anything (I never use the Windows meta keys, or maybe I don't know what they're for, and I don't think I use the right Alt key) and figure out how to remap keys like that at the moment.
Thanks for the help. I thought I'd installed all the Korean packages, but since I went to Language Support and enabled Korean there (I have no idea why I never tried that before) and logged out and back in, I have full Korean support.

I don't know how to map the keys like you mentioned, but in SCIM setup I was able to configure the Pause key (which has no other use to my knowledge) to toggle between SCIM methods.

---

### Post by phubert28 on 2010-05-19
O.K. Here comes a REAL dummy. Just installed Ubuntu at home for the first time... INSTALLED once at work but never got into it. (64 bit Ubuntu 10.4)

SCIM??? What/where?

Keyboard icon in TRAY???

WHICH tray? (don't see a keyboard icon)

I've installed a number of language packages and under Language & Text, I see Keyboard input method system and none of those means anything to me.

Naturally, I'd want to be able to EASILY switch between English and Korean and back again (studying the latter) - was quite easy under Windows (crashed which is why I'm on Ubuntu!)

---

### Post by Dkkline on 2010-05-19
Not really sure what you mean (might be my bad english tho...)
Well not really sure if this helps anyway but give it a go

Try go "System -> Preference -> Keyboard" then click the "Layouts" tab, then "Add" then select Korean or whatever you want, then click "Apply System-Wide..."

Hope this helped, Good Luck with your Korean!

---

