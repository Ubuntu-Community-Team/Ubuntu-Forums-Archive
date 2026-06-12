---
title: "Pidgin and the fast user switching applet in 9.04"
date: 2009-04-18
forum: General Help
---

### Post by lost. on 2009-04-18
When pidgin is running, it transforms the user switching applet into a pidgin status / user switching applet (better described here: [http://www.markshuttleworth.com/archives/233]("http://www.markshuttleworth.com/archives/233")). Does anyone know how to turn this feature off?

---

### Post by st000 on 2009-04-26
I was able to edit the configuration for fast-user-switch-applet to disable the sub-menu that is displayed when logged into pidgin.

 - Open the Configuration editor in administrator mode
```
user@computer > gksudo gconf-editor
```
 - browse to /apps/fast-user-switch-applet
 - uncheck show_presence_info

I wasn't able to disable the presence icon (green circle for online, red for offline, etc..) displayed by the fast-user-switch-applet with this configuration change.

---

### Post by Crowder on 2009-04-28
this is somewhat unrelated, but I didn't want to start a whole new thread unnecessarily.

I agree that the new pidgin feature is kind of useless (especially since you can do the same thing from the system tray or add a plugin to go away on lock, etc.), but I mainly think so because it does nothing other than control Pidgin. Do you think there's any way this could be modified to work with other applications? It might actually prove useful if it could change status in other networking tools - like skype or something. I don't know.

---

### Post by st000 on 2009-04-28
The integration should be **optional!**

---

### Post by Crowder on 2009-04-29
i don't get what the huge issue is, you can just not click those buttons.... and besides there's already a simple solution to disable it below, so it would seem that it *is* optional.

---

### Post by XxsydenxX on 2009-04-29
In my opinion the feature itself is just plain stupid, its pointless...its just integrating a already good system into the os itself..so if you dont want said feature of the os such as fast user switch applet...then you loose functionality of pidgin because the icon for pidgin nolonger shows up in the notification area, any fixes for this?

---

### Post by JK3mp on 2009-04-29
ick...sounds like  a dumb ploy :(

---

### Post by julie20099 on 2009-04-29
I like that new fusa applet, because they implemented something I had wished for a long time - you now can tell with one applet what you current status is and it tells that different applications like pidgin and empathy. Like the clock applet that now also shows weather information this allows the user to have less applets on his panel. This is exactly the right direction.

_____________________________________

[cheap uggs](http://www.inugg.co.uk)
[hair cuts durham nc](http://salon168.com/seethematwork.htm)

---

### Post by Crowder on 2009-04-29
> **XxsydenxX said:**
> In my opinion the feature itself is just plain stupid, its pointless...its just integrating a already good system into the os itself..so if you dont want said feature of the os such as fast user switch applet...then you loose functionality of pidgin because the icon for pidgin nolonger shows up in the notification area, any fixes for this?

But I still have an icon in the notification area... :confused:

You're right, it is redundant - and if your icon is gone then it's probably a major pain. 

Maybe you disabled it yourself? Try going to Tools ---> Preferences.
You should see in the main "interface" tab a menu for the system tray icon. Make sure it's set to "Always" if you want to see a Pidgin icon in the tray.

Does this fix your problem?

---

### Post by Crowder on 2009-04-29
> **julie20099 said:**
> I like that new fusa applet, because they implemented something I had wished for a long time - you now can tell with one applet what you current status is and it tells that different applications like pidgin and empathy. Like the clock applet that now also shows weather information this allows the user to have less applets on his panel. This is exactly the right direction.


I (sort of) agree, but I also like the Pidgin icon. And as I said before, it would be nice to see that function working with other applications as well, so that it wasn't completely pointless.

---

### Post by st000 on 2009-04-29
> I like that new fusa applet

> I (sort of) agree, but I also like the Pidgin icon

> In my opinion the feature itself is just plain stupid, its pointless

> ick...sounds like a dumb ploy

> I agree that the new pidgin feature is kind of useless 

This is why, IMHO, there should be an option to disable/enable pidgin integration with Fast User Switching Applet.

---

### Post by skeetre on 2009-04-29
I hate the new Pidgin icon. I thought it was for Evolution. The icon looks like a mail envelope. I also liked the old way where I could double click on the icon to minimize the contacts list, or to reopen the contacts list. Now I have to click on the icon once, then click on the Pidgin menu item that comes up. Also before I could right click on the icon to exit the program. Now I have to open the contacts list then go to buddies, and then quit. Very Annoying. I also liked the way the pidgin icon looked.
Thanks for pointing out how to disable the pidgin integration.

---

### Post by Crowder on 2009-05-01
> **skeetre said:**
> I hate the new Pidgin icon. I thought it was for Evolution. The icon looks like a mail envelope. I also liked the old way where I could double click on the icon to minimize the contacts list, or to reopen the contacts list. Now I have to click on the icon once, then click on the Pidgin menu item that comes up. Also before I could right click on the icon to exit the program. Now I have to open the contacts list then go to buddies, and then quit. Very Annoying. I also liked the way the pidgin icon looked.
Thanks for pointing out how to disable the pidgin integration.

that's actually something else. you're talking about the new indicator-applet. 

check out this thread: [http://ubuntuforums.org/showthread.php?t=1138562]("http://ubuntuforums.org/showthread.php?t=1138562")

and again, the normal pidgin icon should still be there. if it's not, check your preferences and make sure it's set to "always" instead of "never."

---

### Post by Crowder on 2009-05-01
> **st000 said:**
> This is why, IMHO, there should be an option to disable/enable pidgin integration with Fast User Switching Applet.

well, your solution did work, right?

[QUOTE=st000]I was able to edit the configuration for fast-user-switch-applet to disable the sub-menu that is displayed when logged into pidgin.

- Open the Configuration editor in administrator mode
Code:

user@computer > gksudo gconf-editor

- browse to /apps/fast-user-switch-applet
- uncheck show_presence_info

I wasn't able to disable the presence icon (green circle for online, red for offline, etc..) displayed by the fast-user-switch-applet with this configuration change.[/QUOTE]

---

### Post by weboide on 2009-05-12
The 'gksudo' should be omitted! This is totally unnecessary.

---

### Post by evanrmurphy on 2009-05-12
> **st000 said:**
> I wasn't able to disable the presence icon (green circle for online, red for offline, etc..) displayed by the fast-user-switch-applet with this configuration change.

So, is the verdict that there's no way to completely disable FUSA integration with applications like Pidgin and Empathy, even after unchecking the show_presence_info box in gconf-editor? That removes the presence options from the FUSA dropdown, but it doesn't keep these applications from changing the visible icon from the the red shutdown button to an icon reflecting the user's presence info.

---

### Post by dbstraight on 2009-05-13
> **evanrmurphy said:**
> So, is the verdict that there's no way to completely disable FUSA integration with applications like Pidgin and Empathy, even after unchecking the show_presence_info box in gconf-editor? That removes the presence options from the FUSA dropdown, but it doesn't keep these applications from changing the visible icon from the the red shutdown button to an icon reflecting the user's presence info.
Sigh. I've almost stopped using Pidgin because of this obnoxious junk. I wish there was a universal option "don't let ANY program touch my system stuff; just keep them the hell out."

---

### Post by mihai.ile on 2009-05-18
right now it's impossible to keep the icon to default red button. Pidgin change it even with the option unchecked in gconf-editor.
This option is:
1: annoying!
2: not user firendly
3: redundant

Did anyone managed to block pidgin not to change it or something?

---

### Post by chocobanana on 2009-05-18
Greetings

For those who don't like the new Pidgin integration in the "system tray", just remove the Indicator applet (with the letter icon) when it shows up in the screen. The Pidgin icon should then come back. :)

Alternatively it can be re-enabled in the Pidgin preferences under the Interface section.

---

### Post by mihai.ile on 2009-05-18
> **chocobanana said:**
> Greetings

For those who don't like the new Pidgin integration in the "system tray", just remove the Indicator applet (with the letter icon) when it shows up in the screen. The Pidgin icon should then come back. :)

Alternatively it can be re-enabled in the Pidgin preferences under the Interface section.

This is not about the indicator applet, it's about fast user switching applet, wrong thread maybe.

---

### Post by evanrmurphy on 2009-05-18
I learned from [this entry on My Green Life]("http://www.peppertop.com/blog/?p=218") that if you remove FUSA from the panel, then the options for Log Out, Lock Screen and Shut Down will reappear in the System menu where they were on earlier releases of Ubuntu. This has the advantage of eliminating FUSA from view if you don't like some of its behaviors (e.g. presence-info interaction with Pidgin), in addition to providing a way to log out from the keyboard, because I don't think there's a keyboard shortcut to access FUSA and the Ctrl+Alt+Backspace combination to zap X was disabled by default in Jaunty.

The above doesn't address this thread's main issue, but I thought it was relevant and that some people may find it a productive workaround.

---

### Post by eznet on 2009-05-31
> **chocobanana said:**
> Greetings

For those who don't like the new Pidgin integration in the "system tray", just remove the Indicator applet (with the letter icon) when it shows up in the screen. The Pidgin icon should then come back. :)

Alternatively it can be re-enabled in the Pidgin preferences under the Interface section.

Although I know this is not the thread - Thanks, Chocobanana, that was exactly the answer I needed!

---

