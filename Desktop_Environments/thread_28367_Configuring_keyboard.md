---
title: "Configuring keyboard"
date: 2005-04-19
forum: Desktop Environments
---

### Post by magemaster on 2005-04-19
Hello all!

I am a brazilian user with a United States Keyboard(Logitech Elite)
How can I configure the ubuntu to brazilian and the keyboard to us

Ps> My menus are really in portuguese, what I want is the 'ç' , 'ã' , 'é'...

---

### Post by Alexander Kirillov on 2005-04-20
[QUOTE=magemaster]Hello all!

I am a brazilian user with a United States Keyboard(Logitech Elite)
How can I configure the ubuntu to brazilian and the keyboard to us

Ps> My menus are really in portuguese, what I want is the 'ç' , 'ã' , 'é'...[/QUOTE]
 - to configure Ubuntu to use Portuguese (Brazilian version), select appropriate language in GDM login screen (Options - or Languages ? - menu at the bottom of the screen, if I remember correctly) 

- to change keyboard layout, choose the menu System->Preferences->Keyboard. If you wnat to switch between several layouts, you might also add Keyboard indicator applet to your panel. 

- to use accents, you can use the usual US keyboard, but in System->Preferences->Keyboard-Keyboard options, select one of options for "compose". E.g., if you select "Right Alt", then, to enter é, press RightAlt+', then press e.

---

### Post by magemaster on 2005-04-20
Can I enable compose by default??????????

---

### Post by Alexander Kirillov on 2005-04-22
[QUOTE=magemaster]Can I enable compose by default??????????[/QUOTE]
  After you made changes in System->Preferences->Keyboard-Keyboard options, they become permanent. You will have compose on the next time you login - you will not have to do anything. 

(Wouldn't work at login screen, though)

---

### Post by easy_target on 2005-10-21
I think what he meant is to enable a keyboard with dead-keys by default, where '+c makes cedilla and so on. I have this very same question but when I try to install US with dead-keys the theme changes to Gnome default and keeps flickering. What's wrong?

---

### Post by melissawm on 2005-11-19
I have the exact same problem - themes changing and screen flickering. I'm also Brazilian but living in Belgium, so I _really_ need the cedilla. The thing is, if I go to the Keyboard Options and select "US International (with dead-keys)" the accents all work, look:
é á ó ú 
etc... but I get &#263; instead of cedilla when I type '+c. 

Any ideas???

I already had this problem with hoary, and I could only fix it by installing the WHOLE ubuntu in french... I think there should be an easier way to do it...

---

### Post by spier on 2005-12-06
Same problem here: Needing to type in Brazilian flavor, but when trying to set  compose key, "themes changing and screen flickering". Really annoying.  May a downgrade to 5.04 be an option?

---

### Post by simosx on 2006-01-28
[QUOTE=spier]Same problem here: Needing to type in Brazilian flavor, but when trying to set  compose key, "themes changing and screen flickering". Really annoying.  May a downgrade to 5.04 be an option?[/QUOTE]

You normally do not need to change the compose key, as the default is RightAlt and quite sufficient.
In any case, such strange behaviour looks like a bug that should be reported to the Bug reporting system of Ubuntu ([http://bugzilla.ubuntu.com/)](http://bugzilla.ubuntu.com/)).

I got Brazilian Portuguese to work very easily with the instructions at
[http://planet.hellug.gr/misc/bra/](http://planet.hellug.gr/misc/bra/)

---

### Post by ispmarin on 2006-02-08
This maybe is a solution, but a terrible one. We, brazilian speakers are _VERY_ used to type '+c to get cedila. We _DONT_ want to type ; for cedila or AltGr for that.  Therefore must be a solution for this problem. And a urgent one, because this is really annoying and the problem persists for a long time now.

---

