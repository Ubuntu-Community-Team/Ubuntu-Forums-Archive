---
title: "Accent characters and the Spanish keyboard layout"
date: 2006-07-30
forum: Desktop Environments
---

### Post by bennybobw on 2006-07-30
I need to be able to write things in Spanish I'm having trouble making the characters with accent marks, (e.g. é). For instance, this character comes out as ´e. 
I found [this post]("http://www.ubuntuforums.org/showthread.php?t=94457&page=1") (from what I understood) where they figured out that it was a bad xkeyboard config file.
Someone "tracked down" a newer version in the Debian repositories, but did not post a link or instructions about how to get it. 
1) Could someone tell me how to do this?
2) It seems as though this should be updated in the Ubuntu repository as well (it didn't work in Breezy either)

On the other hand, maybe I didn't quite understand the solution in the other thread.  I'm using gnome not KDE and I have no idea what a SCIM or a C_CTYPE environment variable is.

Thanks for your help.

--bennybobw

---

### Post by jordilin on 2006-07-30
At the login entry screen you can choose the language of your system. Perhaps choosing Spanish solves your problem. Just try it, and tell us sth. Hope it will work :D

---

### Post by arkangel on 2006-07-30
system>> preferences >> keyboard >> layout  
then press  Add,  look for spanish , add it and mark it  as default . That will do the trick inmediatelly

---

### Post by bennybobw on 2006-07-30
I tried both of these suggestions and neither of them worked.  I´m still getting ´e instead of é. I can type ñ without any problem, it seems like the keystroke combinations are the issue. 

--bennybobw

---

### Post by orlox on 2006-07-30
I have a QWERTY spanish keybord (e.g. if you read the first line of letters it reads QWERTY), and I have set a spanish keyboard layout. to make an accent, I press the key that's at the right of the ñ, and then press the letter I want with an accent....

---

### Post by bennybobw on 2006-07-30
Yes, that's exactly what I'm doing and it gives me the accent followed by the letter.  I'm using a QWERTY keyboard as well.  I´m also sure that the keyboard is set to Spanish because I can make ñ, etc. and the keyboard indicator displays "ESP".  Is there some other setting I have to change to make it work?  

--bennybobw

---

### Post by adamkane on 2006-07-31
This has been a problem for like forever. The problem is that most users don't have foreign keyboards, so it is up to those of you that do to figure out the solution, and share it with the rest of us.

Let us know how things turn out.

[http://www.ubuntuforums.org/showthread.php?t=102760](http://www.ubuntuforums.org/showthread.php?t=102760)
[http://www.ubuntuforums.org/showthread.php?t=102778](http://www.ubuntuforums.org/showthread.php?t=102778)
[http://www.ubuntuforums.org/showthread.php?t=129860](http://www.ubuntuforums.org/showthread.php?t=129860)

---

### Post by jordilin on 2006-07-31
Two possible solutions.
First, and I don't know if it will work, is saving the documents with the ISO-8859-15 charset.
Secondly, this will work for sure, is reinstall Ubuntu with the Spanish language. Then you'll have your keyboard configured and will be able to switch between spanish and english

---

### Post by bennybobw on 2006-08-01
I've discovered that if I enable the French keyboard, for example, I don't have any problem with using the key combinations to type an accented character.  The problem seems to be with the Spanish keyboard file itself.  Also, I failed to mention before that I don't actually have a Spanish keyboard and I'm working on a IBM Thinkpad T41.
I'm not sure where to go next to try to figure this out.  I looked up the xkeybord-config and Dapper uses the very latest version.  Anyone have any ideas?

---

### Post by arashiko28 on 2008-03-09
I have the exact same problem, except for the fact that until yesterday I had a spanish layout keyboard. I reinstalled gutsy out of fancy to test Ubuntu Ultimate 1.7 and forgot to set the spanish layout when installing the OS. Now, I'm not interested into having the entire system on spanish, why? Because you get lost in translation. Besides, I also need the japanese layout, but that's another thing. Right now, I have reconfigured my keyboard about a 150 times. I have done it in system - preferences - keyborad, I have added the language support for english, french, esperanto, spanish, german, greek, latin (i think that's all) I can write ñ, Ñ. But need the accents, ´a, ´e, ´i, ´o, ´u. and the dieresis (don't know the name in english) ¨a, and so on.
Even if spanish is my native language, computers are other deals and it's pretty odd to translate from a book what the author wants you to do and find that in a diffenrent language.
I have HP Pavilion ze2000, us model. pc105 keyboard.

---

### Post by barlaventoexpert on 2008-03-10
I've got the same problem here.

I live in Portugal and have an Acer Aspire 4310.

I installed Gutsy 7.10 several months ago and the keyboard was fine, including the Portuguese accent keys which I need when writing Portuguese.

I recently installed SCIM to read some chinese fonts and thereafter voila no Portuguese accent keys.

I've spent hours looking for a solution including changing languages and keyboard options...to no avail.

I need these keys but am going to wait until Hoary is out next month and do a new reinstall.

It is an annoying bug however.

---

### Post by simosx on 2008-03-16
> **barlaventoexpert said:**
> I've got the same problem here.

I live in Portugal and have an Acer Aspire 4310.

I installed Gutsy 7.10 several months ago and the keyboard was fine, including the Portuguese accent keys which I need when writing Portuguese.

I recently installed SCIM to read some chinese fonts and thereafter voila no Portuguese accent keys.

I've spent hours looking for a solution including changing languages and keyboard options...to no avail.

I need these keys but am going to wait until Hoary is out next month and do a new reinstall.

It is an annoying bug however.

In general, to type in different languages you may found these posts useful,
[http://blogs.gnome.org/simos/2008/02/03/typing-squiggles-and-dots-in-gnome-and-gtk-applications/](http://blogs.gnome.org/simos/2008/02/03/typing-squiggles-and-dots-in-gnome-and-gtk-applications/)

The problem with SCIM is that when it is activated, it cuts off the dead_key support in GNOME.

How do you activate/deactivate SCIM? There is this shortcut, Ctrl-Spacebar.With this, you can toggle on and off SCIM. When you off SCIM, then the default GNOME input method is back in control (GTK+ Input Method), and you can type dead keys.

You only need SCIM when you want to type complex languages (such as Chinese). If you do not need to write Chinese, take SCIM off.

The current test version of Ubuntu 8.04 has SCIM available by default, and people press Ctrl-spacebar by accident, and it messes up everything...

---

