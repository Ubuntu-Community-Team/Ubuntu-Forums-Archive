---
title: "What to do when the Options button (“Cog wheel”) disappears in nautilus from the uppe"
date: 2015-01-28
forum: Desktop Environments
---

### Post by ldp06000 on 2015-01-28
[COLOR=#333333][FONT=UbuntuRegular]I noticed that sometimes the "Cog Wheel" - Options button (I do not know if it is the proper translation from French) at the most up-right corner disappears in nautilus (see attached image) Without Option button : [/FONT][/COLOR][ATTACH=CONFIG]259563[/ATTACH]

[COLOR=#333333][FONT=UbuntuRegular]I tried to stop and restart Nautilus via the "nautilus -q && nautilus &" command found in the following [How to restart nautilus without logging out]("http://askubuntu.com/questions/19979/how-to-restart-nautilus-without-logging-out") but this DOES NOT make the Options button re-appear.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In the contrary it gives me the following error message :[/FONT][/COLOR]> [INDENT]nautilus -q && nautilus & [1]("http://i.stack.imgur.com/1ex3v.png") 4700 laurent06000@PC-DE-LDP:~$ Impossible d'enregistrer l'application: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
[/INDENT]
[COLOR=#333333][FONT=UbuntuRegular]Which can be translated to "Impossible to register the application : ..."[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The only workaround I found is to restart ubuntu which is not an acceptable solution (even closing and opening the session doesn't solve this problem).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any help would be greatly appreciated.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Laurent[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][Edit 1] : I confirm that after a crash of Nautilus I do not see the Option Button anymore as described above and I have to restart .[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]And when I issue the command "nautilus -q && nautilus" I still receive the message[/FONT][/COLOR]
> [COLOR=#333333][FONT=UbuntuRegular]laurent06000@PC-DE-LDP:~$ nautilus -q && nautilus[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Impossible d'enregistrer l'application:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]GDBus.Error:org.freedesktop.DBus.Error.NoReply:[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular] Message did not receive a reply (timeout by message bus)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][Edit 2] : after all latest updates applied I now DO NOT have the Options Button in Nautilus even after a Ubuntu restarted from fresh.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This is REALLY annoying because this button allows for example to automatically select files from formating rules (+ invert the selection) and many other power full options).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any idea ?

Laurent[/FONT][/COLOR]

---

### Post by mc4man on 2015-01-28
Your 1st screen with cog & view buttons isn't anything seen in any recent ubuntu (14.04/13.10/14.10) when on an ubuntu session  plus there is no window decoration nor a close button
Your 2nd screen is more like what you should see in recent ubuntu, (ubuntu session)  except again no window deco. ( the cog & view options are in nautilus's menus in panel

So - 
What release of Ubuntu are you using
What session, run this to check
```
echo $DESKTOP_SESSION
```

Nautilus in a gnome session would have the cog & view buttons but may not work correctly with the default ubuntu ambiance theme

---

### Post by ldp06000 on 2015-01-28
I run the 14.04 release and the [COLOR=#000000][FONT=Ubuntu Mono]echo $DESKTOP_SESSION command gives me ubuntu.

I must say I'm surprised to read that the Cog (Options button) doesn't exist on Ubuntu 14.04. I did not install anything above the standard version and I DO have for example the option to select files via rules (* ?) for example  : screen??.*  [/FONT][/COLOR]

---

### Post by deadflowr on 2015-01-28
> **ldp06000 said:**
> I run the 14.04 release and the [COLOR=#000000][FONT=Ubuntu Mono]echo $DESKTOP_SESSION command gives me ubuntu.

I must say I'm surprised to read that the Cog (Options button) doesn't exist on Ubuntu 14.04. I did not install anything above the standard version and I DO have for example the option to select files via rules (* ?) for example  : screen??.*  [/FONT][/COLOR]

I think what mc4man meant was that the cog isn't really needed in Ubuntu(unity session) because the cog's features are in the unity global menu, so it is removed from nautilus running in unity. The global menu is located in the top panel of the desktop screen. You need to hover the mouse over the left side area of the top panel and the menu will come into focus, otherwise the area will only show you the currently running program's name.

You can also access specific menu items by pressing the alt button to invoke the HUD, which you can then use the keyboard to do a quick search and launch for specific menu items/functions, like open a new window or what have you.

Hope this makes sense and clears up a little on how unity/Ubuntu work.

---

