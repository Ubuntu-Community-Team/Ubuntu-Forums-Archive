---
title: "Foreign Language Support"
date: 2012-09-01
forum: Desktop Environments
---

### Post by wrknight on 2012-09-01
I recently installed ubuntu 12.04 with gnome classic and set it up to use 2 foreign language keyboard layouts; one russian and one spanish.  A little while ago, my computer rebooted while I had the Spanish keyboard layout.  When the system came back up, all the desktop information (menus, commands, etc) was in a combination of Russian and Chinese (it might have been Japanese, I can't tell the difference.)  I have never installed Chinese and I have no idea how it got into my system.  I was able to restore English for about 90% of the desktop, but there's still 10% that is in either Chinese or Russian and I can't find a way to get rid of it. 

At this point, I would like to get rid of all foreign language support and all foreign language fonts, but I can't figure out how to do that. 

Chinese language shows up in the language support gui under the "language" tab and the "regional formats" tab but it is grayed out and I cannot remove it.  It also shows up in the keyboard layout gui under the "language" tab and the "system" tab where it shows Chinese as the display language under "your settings" and "system settings".

---

### Post by OM55 on 2012-09-01
It sounds like you unknowingly changed the interface language... Sadly it is not too hard to do in Ubuntu 12.04 and they should really correct this behavior.

Here is what you need to do (and some additional explanation). Please read through first and try to repair - after:

Go to: "System Settings -> Keyboard Layout". Notice that there are two icons  starting with the name 'Keyboard' so make sure you select the correct  one: "Keyboard Layout" - at the top.

**IMPORTANT:** The initial screen (the "Language" tab) shows a  list of a few languages. Those are the interface languages. If your current interface language was changed and is not English, the list may not show up in a readable language to you (i.e. Chinese, Japanese etc.)

**To solve your problem**: click and highlight the last name on the list (English USA), then close and restart your computer. Your interface should be all back to English.

To remove the additional languages: Go again to "System Settings -> Keyboard Layout" Select the "Layouts" tab, highlight the language you want to remove and then click on the "-" sign at the lower left corner.


[I]**Explanation:** The way this "Language" tab works, is that the language that is highlighted when this Keyboard Layout dialog is closed, will be the language that will load after the next reboot. There is NO other indication or notification to the user that a language interface change was made! To make things worse - once the interface language has changed, there is no shred of common language (like English) to let you go back to the English (or your preferred) language interface...

Normally **BE VERY CAREFUL _NOT_ to click **on any of the languages in the (of if you do, click on your English right after) because the interface language change  is _**accepted**_ as soon as you highlight the language with no other indication to the user, but _**will become effective**_ only  after the next reboot. However, unless you are fluent with all the those  languages, you might find yourself with a completely localized foreign language interface  without being able to read the even the names of the languages in order to click and change the interface back to  English... 
(every multilingual website would always keep an "English" icon visible at all times, while here the Ubuntu programers... forgot).

As a result, many users accidentally highlight the a foreign language, nothing happens so they assume all is fine and forget about it, just to face a foreign language interface after a reboot down the rode, without easy (English) ability to switch back...
After the second time this happened to me I simply translated (using Google Translate) the visible language names from Chinese to English and then clicked on the right one...
[/I]
Anyway, hope that helps!

---

### Post by wrknight on 2012-09-01
_**Problem Solved**_

Found 4 different configuration files that were conflicting and each time I rebooted, my desktop would come up in another language (3 times out of 4 it was Chinese).  The first two were system configuration files, the third file was a gnome file (that's the one that was overwriting the system configuration files) and the last one was a Skype configuration file.

The files were

/etc/environment
/etc/default/locale
/home/account/.pam_environment
/home/account-name/.Skype/shared.xml

The first three files must have LANG (and/or LANGUAGE) = en_US.UTF-8 and all the other language options must be consistent.  In my case, they were totally mixed up with Russian, Spanish and Chinese.

The last file was a configuration file for Skype written in html and toward the bottom is a configuration block that must specify <Language>en</Language> "or preferred language".  This file was not used to overwrite any others, but cause Skype to open up in Russian.  (very inconvenient)

The Skype file didn't affect anything except the Skype application, but the gnome file .pam_environment was used by gnome to rewrite both LANG= instruction in /etc/environment and in /etc/default/locale files.

---

### Post by wrknight on 2012-09-02
Related to the Language support question, I find that Chinese is still listed in the language lists of the **System Settings -> Language Support** and in the **System Settings -> Keyboard Layout -> Language** configuration controls.  While I can add as many languages as I want to either of these lists, I cannot remove any of them.  In particular, Chinese is listed in both lists, and on two occasions since installing 12.04, my desktop environment has opened up in Chinese after re-booting.  

While I have fixed the problem for now, I would like to find out how to prevent it.  In particular, I would like to find the files containing those lists and manually edit them.  

Does anyone know the names and locations of those files?  Or is there a better approach to the problem?

Secondly, I am not sure that I need or want iBus on my system since I only want to change my keyboard layout.  Can anyone tell me what iBus is doing for me, why I need 2 keyboard icons on my panel and why I shouldn't quit iBus and/or remove iBus from my system?

---

### Post by pressureman on 2012-09-18
I just did a clean install of Ubuntu 12.10 beta1 yesterday from the desktop/live CD. I also see what appears to be Chinese shown in the list of supported languages.

However if I click the button to add/remove language packs, I only see English (which came from the installer), and German, which I later added myself. No Chinese.

Where is it coming from?

I also had to manually edit my /etc/default/locale, which had no setting for LANG, and also edit my ~/.pam_environment, which had somehow picked up the Chinese setting for LANGUAGE and LANG - albeit a corrupt mish-mash of zh_CN and en_US. The "Language Support" and "Keyboard Layout" settings apps definitely appear to be somewhat buggy.

---

