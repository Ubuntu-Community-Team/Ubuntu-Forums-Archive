---
title: "how do I disable the print screen button?"
date: 2007-03-23
forum: Desktop Environments
---

### Post by rlklee on 2007-03-23
I have been trying to get my print screen button in KDE disabled for a while now.  It is no where to be found as activated in the keyboard shortcuts in the control panel.  It is very annoying as it is located above my backspace key and every time I mis-press ksnapshot comes up.  Argh.  

How might I go about tracking this problem down?

Thanks much.

---

### Post by ceeg on 2007-03-23
You can try playing around with the settings in ksnapshot. I'm sure there's an option somewhere to disable it automatically popping up.

If not, just apt-get remove ksnapshot?

---

### Post by rlklee on 2007-03-23
I've actually done both of the suggested already.  Now what happens is konqueror pops up as "locate:ksnapshot".....

---

### Post by JuhazOne on 2007-04-16
This is something I'd like to know, too. I can understand why someone would want to make Print Screen launch Ksnapshot by default, but I can't understand why it has to be so difficult to disable this behavior. I tried xmodmap to disable the key altogether but to no avail, I tried taking away execute permissions (and I get this locate-popup) and I tried replacing the binary with a shell script that doesn't do anything (and now I get an error).

Using Dapper btw.

---

### Post by woidi on 2007-04-24
how about  Control Center / Regional & Accessibility / Input Actions / Preset Actions / PrintScreen / Disable

---

### Post by JuhazOne on 2007-04-24
> **woidi said:**
> how about  Control Center / Regional & Accessibility / Input Actions / Preset Actions / PrintScreen / Disable

That one didn't work for me. Besides disabling PrintScreen I also tried deleting the whole action. **However**, after these I checked the Disable checkbox in Control Center / Regional & Accessibility / Input Actions / ksnapshot. After all this, Print Screen doesn't do anything anymore. :)

I'd never have thought to look there, so thanks. :)

Oh, and I'm using Feisty now.

---

### Post by rungss on 2007-11-12
> **JuhazOne said:**
> That one didn't work for me. Besides disabling PrintScreen I also tried deleting the whole action. **However**, after these I checked the Disable checkbox in Control Center / Regional & Accessibility / Input Actions / ksnapshot. After all this, Print Screen doesn't do anything anymore. :)

I'd never have thought to look there, so thanks. :)

Oh, and I'm using Feisty now.

I am using Gutsy Gibon (7.10)
I dont see the Regional & Accessibility Settings in teh Control Center..

How do I do it??
I need it very badly... 

Thanks

---

### Post by rungss on 2007-11-12
Ok I resolved it..

From System -> Preferences -> KeyBoard Shortcut

In the Desktop Section I just changed the Keyboard Shortcut for **"Take a Screenshot"**
 from Print to **Control + Alt + P**

Do post if you find any other Solution...

Thanks,

---

