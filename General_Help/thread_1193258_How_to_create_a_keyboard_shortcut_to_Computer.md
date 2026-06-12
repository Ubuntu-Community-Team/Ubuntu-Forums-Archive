---
title: "How to create a keyboard shortcut to Computer"
date: 2009-06-21
forum: General Help
---

### Post by KarenAK on 2009-06-21
Being still used to the Windows+E shortcut to the Windows Explorer, I would like to create a similar shortcut to "Computer" but cannot seem to find any info about this.

Can anybody tell me how to do this ?

Thank you in advance :-)

---

### Post by celticbhoy on 2009-06-21
Goto System --> Preferances --> Keyboard shortcuts
Click ADD
Give it any name you want, and for command enter'nautilus' without quotes.
then navigate to the bottom of the list and click on your entry and then hold down your key combination.

---

### Post by KarenAK on 2009-06-21
I checked this before but there is no ADD button, so I assumed one could only modify the existing ones.

Edit: also the help file says nothing about adding shortcuts

---

### Post by celticbhoy on 2009-06-21
Strange!

Can you post a screenshot of your keyboard shortcuts screen please.

---

### Post by KarenAK on 2009-06-21
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]http://i107.photobucket.com/albums/m312/KarenAK/Temp/KeyboardShortcuts.png[/IMG]

---

### Post by VCoolio on 2009-06-21
Actually there is an add button. But your problem is going to be that you can't fill in a key combo with the windows key. So open the configurations editor (Applications > System tools) and do it manually. Navigate to apps > metacity. Under global_keybindings there are some run_command_xx entries which correspond to the commands you assign to the command_xx entries under keybinding_commands. So for example make run_command_1 "<mod4>e" (without the "") to represent windowskey+e and make command_1 "nautilus ~/" which will open nautilus in your home folder.

Edit: hm no add button for you then. Peculiar. Anyways, my howto holds I guess.

---

### Post by celticbhoy on 2009-06-21
What version of Ubuntu you running ??

There should be an option in the keyboard shortcuts for home forlder & you could change that to <super> E as a temp measure, it just means that nautilus will start in your home directory.

---

### Post by VCoolio on 2009-06-21
celcbhoy, no that's exactly what he can't do. See the [bug]("https://bugs.launchpad.net/bugs/12153") I was talking about. Unless you guys don't suffer from the bug of course.

---

### Post by KarenAK on 2009-06-21
Thank you very much for that info !

It doesn't work with <mod4>e but <Control>e works ok. However, that's not important just so long as I DO have a shortcut and know how to create more of them :-)

(VERY strange though that there's no ADD button....)

---

### Post by KarenAK on 2009-06-21
Ubuntu 8.10

---

### Post by celticbhoy on 2009-06-21
There is at this point nothing to suggest that this bug will cause a problem on this system, so it must be worth a try. I think the bigger issue at the mo, is why there is no option to add.

---

### Post by KarenAK on 2009-06-21
<Super>e doesn't work either. 


FYI

I installed Intrepid Ibex because I couldn't get the new version to run on this laptop. I did the default install, tried nothing fancy. So this should be a very average installation of Gnome and its apps.

---

### Post by VCoolio on 2009-06-21
If you're into using keybindings use xbindkeys. You can use it to assign any command to any key- / mousebinding. Also the winkey works (with <mod4>).

---

### Post by blueridgedog on 2009-06-21
I too do not have an "add" button, but I edited the "home folder" action to suit my needs.

---

### Post by KarenAK on 2009-06-21
oh gosh, that's a console app....... well, guess it's time to learn how to work with the terminal....:-/

---

### Post by VCoolio on 2009-06-21
you mean xbindkeys? After installing you just edit ~/.xbindkeysrc anyway you like; I use gedit. You can also install xbindkeys-config to have a gui doing the editing for you. Btw after editing run xbindkeys again before it takes effect.

---

### Post by KarenAK on 2009-06-21
ok, xbindkeys-config works fine --- although the windows key doesn't, but I'll ignore that for the moment. Just like I said before, the main thing is to be able to create shortcuts.

Thank you :-)

---

### Post by VCoolio on 2009-06-24
[Elsewhere on this forum]("http://ubuntuforums.org/showthread.php?p=7508726#post7508726") I read something that might help you: system > preferences > Keyboard > Layouts > Layout options at Alt/Winkey behavior check "super is mapped to win". Give it a try.

---

### Post by kriukov on 2010-11-26
On 8.04, I solved this using [this source]("http://forums.linuxmint.com/viewtopic.php?f=90&p=59971&st=0&sk=t&sd=a#p59979"), but instead of "Super_L" I input "<Mod4><Hyper>e" (because the working Win+D shortcut was represented as "<Mod4><Hyper>d" there). After this, the shortcut Win+E works, although it is marked as disabled in Gnome Keyboard Shortcuts.

---

